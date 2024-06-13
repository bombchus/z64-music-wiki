# Custom Envelopes

=== ":material-code-braces: &nbsp;C"

    ```c
    EnvelopePoint gDefaultEnvelope[] = {
        { 1, 32000 },
        { 1000, 32000 },
        { ADSR_HANG, 0 },
        { ADSR_DISABLE, 0 },
    };
    ```

=== ":material-xml: &nbsp;XML"

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

=== ":material-hexadecimal: &nbsp;Binary"

    ```
    0001 7D00 03E8 7D00 FFFF 0000 0000 0000
    ```