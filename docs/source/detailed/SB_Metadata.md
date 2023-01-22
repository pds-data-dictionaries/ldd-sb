# &lt;sb:SB_Metadata&gt;
**REQUIRED**

The *sb:SB_Metadata* class is the top-level, public entry point class
of the Small Bodies dictionary. It provides to metadata
        specific to the techniques and processes of small bodies
        research. In some cases the metadata is supplemental to more
        general metadata contained in other discipline namespaces – metadata that
        should also be present in the product label.
        
The *&lt;sb:SB_Metadata&gt;* is the class that *must* be used to include any and all 
other SB dictionary classes. It contains three major subclasses:

- [&lt;sb:Observation_Parameters&gt;](Observation_Parameters.rst)
- [&lt;sb:Calibration_Information&gt;](Calibration_Information.rst)
- [&lt;sb:Additional_Image_Metadata&gt;](Additional_Image_Metadata.rst)

All subclasses are optional, but not repeatable - use the classes appropriate to the data.
