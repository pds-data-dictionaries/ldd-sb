Small Bodies Dictionary - Outline
##################################################

*<sb:SB_Metadata>* is the public entry point to the Small Bodies namespace. This class 
contains all other SB classes and must be included to use them. Below is a summary 
outline of *all* classes and attributes in the Small Bodies dictionary, in the order
in which they would appear in a label if every single one was used. Most classes 
are optional at the higher levels, and the majority of attributes are optional as
well. 

**Note** that in many cases in which the *<Internal_Reference>* class from the core
*pds:* dictionary is used to reference a related file, the referring Small Bodies
class **requires** a reference to a specific version of that file - a *lidvid_reference*
rather than a *lid_reference*. When either is acceptable, both are listed as 
alternatives in this outline.

<sb:SB_Metadata>

* <sb:Observation_Parameters> 

  * <sb:Exposure>
  
    * <sb:exposure_duration>
    * <sb:exposure_description>
    
  * <sb:Filter>
  
    * <sb:filter_name>
    * <sb:standard_filter_identification>
    * <sb:filter_type>
    * <sb:center_wavelength>
    * <sb:center_wavelength_id_weighted>
    * <sb:short_wavelength_limit>
    * <sb:long_wavelength_limit>
    * <sb:known_short_wavelength_light_leak>
    * <sb:known_long_wavelength_light_leak>
    * <sb:comment>
    * <pds:Internal_Reference>
    
      * <pds:lid_reference> or <pds:lidvid_reference>
      * <pds:reference_type>
      * <pds:comment>
      
  * <sb:Timing>
  
    * <sb:midobservation_time_UTC_YMD>
    * <sb:midobservation_time_UTC_JD>
    * <sb:start_time_UTC_JD>
    * <sb:stop_time_UTC_JD>
    * <sb:comment>
    
* <sb:Calibration_Information>

  * <sb:Raw_Data_Product>

    * <sb:file_name>
    * <pds:Internal_Reference>

      * <pds:livid_reference>
      * <sb:pds_reference_type>
      * <pds:comment>

  * <sb:Calibration_Applied>

    * <sb:bias_subtraction>
    * <sb:dark_current_removal>
    * <sb:flat_field_applied>
    * <sb:scattered_light_correction>
    * <sb:conversion_to_physical_uni>ts
    * <sb:comment>

  * <sb:Calibration_Reference_Files>

    * <sb:comment>
    * <sb:Flat_Field>

      * <sb:file_name>
      * <pds:Internal_Reference>

        * <pds:lidvid_reference>
        * <pds:reference_type>
        * <pds:comment>

    * <sb:Dark_Field >

      * <sb:file_name>
      * <pds:Internal_Reference>

        * <pds:lidvid_reference>
        * <pds:reference_type>
        * <pds:comment>

    * <sb:Bias_Map>

      * <sb:file_name>
      * <pds:Internal_Reference>

        * <pds:lidvid_reference>
        * <pds:reference_type>
        * <pds:comment>

    * <sb:Bad_Pixel_Map>

      * <sb:file_name>
      * <pds:Internal_Reference>

        * <pds:lidvid_reference>
        * <pds:reference_type>
        * <pds:comment>

* <sb:Additional_Image_Metadata>

  * <pds:Local_Internal_Reference>

    * <pds:local_identifier_reference>
    * <pds:reference_type>
    * <pds:comment>

  * <sb:comment>
  * <sb:image_observation_type>
  * <sb:Ancillary_Data_Objects>

    * <sb:comment>
    * <sb:Quality_Map>

      * <pds:Local_Internal_Referemce>

        * <pds:local_identifier_reference>
        * <pds:local_reference_type>
        * <pds:comment>

      * <sb:Quality_Map_Definition>
      
        * <sb:flags_are_bit_flags>
        * <sb:best_quality_value>
        * <sb:Quality_Flag_Definition>

          * <sb:flag_value>
          * <sb:flag_meaning>

      * <sb:comment>

    * <sb:Error_Estimates_Map>

      * <pds:Local_Internal_Reference>

        * <pds:local_identifier_reference>
        * <pds:local_reference_type>
        * <pds:comment>

    * <sb:SNR_Map>

      * <pds:Local_Internal_Referemce>

        * <pds:local_identifier_reference>
        * <pds:local_reference_type>
        * <pds:comment>

  * <sb:Additional_Geometry_Metadata>

    * <sb:comment>
    * <sb:Instrument_Position_Angles>

      * <sb:x_axis_position_angle>
      * <sb:y_axis_position_angle>
      * <sb:z_axis_position_angle>

    * <sb:Geometry_Vector_Time>

      * <sb:position_velocity_vectors>
      * <sb:time_at_target_UTC_YMD>
      * <sb:time_at_target_UTC_JD>

    * <sb:Per_Frame_Metadata>

      * <sb:frame_number>
      * <sb:frame_exposure_duration>
      * <sb:comment>
      * <sb:Midframe_Time>

        * <sb:midobservation_time_UTC_YMD>
        * <sb:midobservation_time_UTC_JD>
        * <sb:delta_time_from_sequence_start>

      * <sb:Frame_Pointing>

        * <sb:Instrument_to_J2000_Quaternion>

          * <sb:qcos>
          * <sb:qsin1>
          * <sb:qsin2>
          * <sb:qsin3>
