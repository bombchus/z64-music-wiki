# Custom Envelopes

=== "C"

    ```c
    EnvelopePoint gDefaultEnvelope[] = {
        { 1, 32000 },
        { 1000, 32000 },
        { ADSR_HANG, 0 },
        { ADSR_DISABLE, 0 },
    };
    ```

=== "XML"

    ```xml
    <item address="0" name="gDefaultEnvelope">
      <struct name="ABEnvelope">
        <field name="Delay" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="1"/>
        <field name="Argument" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="32000"/>
        <field name="Delay" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="1000"/>
        <field name="Argument" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="32000"/>
        <field name="Delay" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="-1"/>
        <field name="Argument" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="0"/>
        <field name="Delay" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="0"/>
        <field name="Argument" datatype="int16", ispointer="0"
               isarray="0" meaning="none" value="0"/>
      </struct>
    </item>
    ```