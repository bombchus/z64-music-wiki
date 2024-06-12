# ADSR Code

```c
// set initial adsr values
void AudioEffects_InitAdsr(AdsrState* adsr, EnvelopePoint* envelope, s16* volOut) {
    adsr->action.asByte = 0;   // set initial action to a byte with a value of 0
    adsr->delay = 0;           // set initial delay value to 0
    adsr->envelope = envelope; // set initial envelope value equal to envelope
    adsr->sustain = 0.0f;      // set initial sustain value to 0
    adsr->current = 0.0f;      // set initial current value to 0
    adsr->velocity = 0.0f;     // set initial velocity value to 0
}

// main adsr function for handling envelopes, takes as many sets of instructions as needed
// audiobank/soundfont envelopes have 4 sets of instructions (each delay & arg is 1 set)
f32 AudioEffects_UpdateAdsr(AdsrState* adsr) {
    u8 status = adsr->action.s.status; // set current status

    // current adsr status
    switch (status) {
        // status: ADSR_STATUS_DISABLED
        case ADSR_STATUS_DISABLED:
            return 0.0f; // return a value of 0

        // status: ADSR_STATUS_INITIAL
        case ADSR_STATUS_INITIAL:
            // check if action is hang
            if (adsr->action.s.hang) {
                adsr->action.s.status = ADSR_STATUS_HANG; // set status to ADSR_STATUS_HANG
                break; // continue
            }
        // status: ADSR_STATUS_START_LOOP
        case ADSR_STATUS_START_LOOP:
            adsr->envelopeIndex = 0;                  // set initial envelope index to 0
            adsr->action.s.status = ADSR_STATUS_LOOP; // set status to ADSR_STATUS_LOOP
		    
		// label for ADSR_GOTO
        retry:
        // status: ADSR_STATUS_LOOP (will indefinitely loop until delay value of any index is )
        case ADSR_STATUS_LOOP:
            adsr->delay = adsr->envelope[adsr->envelopeIndex].delay; // set delay to envelope index's delay value
            // check delay for special commands, if none move to default actions
            switch (adsr->delay) {
                // special command delay value 0; jumps to ADSR_STATUS_DISABLED
                case ADSR_DISABLE:
                    adsr->action.s.status = ADSR_STATUS_DISABLED; // set status to ADSR_STATUS_DISABLED
                    break; // continue
                // special command delay value -1; skips to ADSR_STATUS_HANG
                case ADSR_HANG:
                    adsr->action.s.status = ADSR_STATUS_HANG; // set status to ADSR_STATUS_HANG
                    break; // continue
                // special command delay value -2; jumps to "retry:" label
                case ADSR_GOTO:
	                adsr->envelopeIndex = adsr->envelope[adsr->envelopeIndex].arg; // set index to arg value
                    goto retry;                                                    // jump to retry:
                // special command delay value -3; jumps to ADSR_STATUS_INITIAL
                case ADSR_RESTART:
                    adsr->action.s.status = ADSR_STATUS_INITIAL; // set status to ADSR_STATUS_INITIAL
                    break; // continue
                // if the delay value for the current index is none of the above commands
                default:
                    // set delay equal to "delay * updatesPerFrameScaled"
                    adsr->delay *= gAudioCtx.audioBufferParameters.updatesPerFrameScaled;
                    // check if delay is equal to 0; !!checks for delay obtained from the above calc!!
                    if (adsr->delay == 0) {
                        adsr->delay = 1; // set delay to 1
                    }
                    adsr->target = adsr->envelope[adsr->envelopeIndex].arg / 32767.0f; // set starget equal to "arg / 32767"
                    adsr->target = SQ(adsr->target);                                   // set target equal to "target^2"
                    adsr->velocity = (adsr->target - adsr->current) / adsr->delay;     // set velocity equal to "(target - current) / delay"
                    adsr->action.s.status = ADSR_STATUS_FADE;                          // set status to ADSR_STATUS_FADE
                    adsr->envelopeIndex++;                                             // increase current envelope index by 1
                    break;                                                             // continue
            }
            // check if status is not ADSR_STATUS_FADE
            if (adsr->action.s.status != ADSR_STATUS_FADE) {
                break; // continue
            }

        // status: ADSR_STATUS_FADE; moves from current index's loop to next index's loop after delay reaches 0 or less (why is it called fade?)
        case ADSR_STATUS_FADE:
            adsr->current += adsr->velocity; // set current equal to "current + velocity"
            adsr->delay--;                   // get current envelope index delay, then subtract 1
            // check if delay is less than or equal to 0
            if (adsr->delay <= 0) {
                adsr->action.s.status = ADSR_STATUS_LOOP; // set status to ADSR_STATUS_LOOP
            }
            
        // status: ADSR_STATUS_HANG
        case ADSR_STATUS_HANG:
            break; // continue
			
        // status: ADSR_STATUS_DECAY
        case ADSR_STATUS_DECAY: // he's dead jim
        // status: ADSR_STATUS_RELEASE; handles decay after a note is released from being held (controlled by playback.c?)
		case ADSR_STATUS_RELEASE:
		    // set current equal to current - fadeOutVel
		    adsr->current -= adsr->fadeOutVel; // fadeOutVel is equal to decayIndex here? could be equal to updatesPerFramesInv...
		    // check if sustain is currently not 0 and if status is set to ADSR_STATUS_DECAY
		    if ((adsr->sustain != 0.0f) && (status == ADSR_STATUS_DECAY)) {
		        // if the above returns true check if current value is less than sustain; where is sustain changed after initialization?
		        if (adsr->current < adsr->sustain) {
			        adsr->current = adsr->sustain;               // set current equal to sustain
		            adsr->delay = 128;                           // set delay to 128
		            adsr->action.s.status = ADSR_STATUS_SUSTAIN; // set status to ADSR_STATUS_SUSTAIN
		        }
		        break; // continue
		     }

	        // check if current is less than 0.00001
	        if (adsr->current < 0.00001f) {
	            adsr->current = 0.0f;                         // set current equal to 0
	            adsr->action.s.status = ADSR_STATUS_DISABLED; // set status to ADSR_STATUS_DISABLED
	        }
	        break; // continue

		// status: ADSR_STATUS_SUSTAIN
		case ADSR_STATUS_SUSTAIN:
		    adsr->delay--; // get delay, then subtract 1
		    // check if delay value is now equal to 0
			if (adsr->delay == 0) {
			    adsr->action.s.status = ADSR_STATUS_RELEASE; // set status to ADSR_STATUS_RELEASE
		    }
		    break; // continue
	}
	// check if action is decay
	if (adsr->action.s.decay) {
	    adsr->action.s.status = ADSR_STATUS_DECAY; // set status to ADSR_STATUS_DECAY
	    adsr->action.s.decay = false;              // set action.s.decay to false
	}
	// check if action is release
	if (adsr->action.s.release) {
	    adsr->action.s.status = ADSR_STATUS_RELEASE; // set status to ADSR_STATUS_RELEASE
	    adsr->action.s.release = false;              // set action.s.release to false
	}
	// check if current is < 0
	if (adsr->current < 0.0f) {
	    return 0.0f; // return a value of 0
	}
	// check if current is > 1
	if (adsr->current > 1.0f) {
	    return 1.0f; // return a value of 1
	}

	return adsr->current; // return current
}
```