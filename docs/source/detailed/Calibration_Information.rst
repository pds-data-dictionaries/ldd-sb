<./sb:Calibration_Information>
##################################################

| **Cardinality:** *Optional*
| **XPath:** *<sb:SB_Metadata/sb:Calibration_Information>*

This is one of the main subclasses under the <sb:SB_Metadata> public 
class. It is optional and not repeatable.

The *sb:Calibration_Information* class documents what processing steps have been
applied to the data, and links to both the raw data file and the specific calibration
files used to produce the processed product presented in the label. 

The *sb:Calibration_Information* class has three major subclasses:

* :ref:`raw-data-product`
* :ref:`calibration-applied`
* :ref:`calibration-reference-files`

.. _raw-data-product:

*************************
<./sb:Raw_Data_Product>
*************************
| **Cardinality:** *Optional*
| **XPath:** *<./sb:Raw_Data_Product>*

The sb:Raw_Data_Product class identifies the raw data product in the PDS archive
that is the immediate predecessor of the current, processed data product.

<sb:file_name>
  | **Cardinality:** *Optional*
  | **Data Type:** *ASCII Short String*
  
  The *sb:file_name* attribute should contain the name, preferably without path
  information, of the file referenced more formally by a pds:Internal_Reference class
  in the same containing class. The file name is provided as a matter of convenience
  and for use as a validation cross-check when the data are accepted for archiving.
  Path information is unlikely to be useful once the data are archived, and as the
  data are curated both paths and file names may change. Consequently, the logical
  identifier appearing in the pds:Internal_Reference should be considered the
  positive identification of the file in question within the archive, rather than the
  name.

<pds:Internal_Reference>
  | **Cardinality:** *Required*
  | **XPath:** *<./sb:Raw_Data_Product/pds:Internal_Reference>*

  The *pds:Internal_Reference* class provides the formal reference, which in this case must
  include both logicial identifer and version number (the "LIDVID"), for the raw data product
  that is the primary source for this processed data product.

  The *pds:reference_type* attribute must have the value **processed_data_to_raw_data**.

.. _calibration-applied:

****************************
<./sb:Calibration_Applied>
****************************
| **Cardinality:** *Optional*
| **XPath:** *<./sb:Calibration_Applied>*

The sb:Calibration_Applied class provide flags to indicate specific calibration
processes that have been performed, as well as references to files provided with
the archive that were used as part of the processing. The otpional sb:comment field
may be used to note any unusual circumstances.


<sb:bias_subtraction>
  | **Cardinality:** *Optional*
  | **Data Type:** Boolean

  The sb:bias_subtraction attribute should be present and contain the value
  "true" if bias subtraction has been performed as part of the processing
  applied to the data comprising the product.


<sb:dark_current_removal>
  | **Cardinality:** *Optional*
  | **Data Type:** Boolean

  The sb:dark_current_removal attribute should be present and contain the value
  "true" if dark current removal has been performed as part of the processing
  applied to the data comprising the product.

<sb:flat_field_applied>
  | **Cardinality:** *Optional*
  | **Data Type:** Boolean

  The sb:flat_field_applied attribute should be present and contain the value
  "true" if flat fielding has been performed as part of the processing
  applied to the data comprising the product.

<sb:scattered_light_correction>
  | **Cardinality:** *Optional*
  | **Data Type:** Boolean

  The sb:scattered_light_correction attribute should be present and contain the value
  "true" if scattered light correction has been applied as part of the processing
  of the data comprising the product.

<sb:conversion_to_physical_units>
  | **Cardinality:** *Optional*
  | **Data Type:** Boolean

  The sb:conversion_to_physical_units attribute should be present and contain the
  value "true" if the primary data is expressed in physical units once any value
  offset and scaling factor included in the definition of the data structure have 
  been applied.

  Note that the PDS definition of "Calibrated" includes "conversion to physical units", so
  typically this attribute is not technically required. It may be included for convenience or
  when it seems necessary to emphasize when the conversion has or has not beed applied.

<sb:comment>
  | **Cardinality:** *Optional*
  | Data_Type: *UTF-8 Text*
  
  A free-format text field to note any unusual circumstances.

.. _calibration-reference-files:

**********************************
<./sb:Calibration_Reference_Files>
**********************************
| **Cardinality:** *Optional*
| **XPath:** *<./sb:Calibration_Reference_Files>*

The sb:Calibration_Reference_Files class provides explicit references to key
calibration files provided as part of the archive. Note that these references
are required to be to specific versions of calibration files, as calibration
processes and details typically evolve over time. The optional sb:comment 
should be used to note any unusual circumstances related to the calibration 
files as a group. The optional pds:comment field in the pds:Internal_Reference 
class should be used to note any unusual circumstances related to any particular 
referenced file. The subclasses mat be listed in any order, and may be repeated
if that makes sense - although that should be explained in a "comment" field.

<sb:comment>
  | **Cardinality:** *Optional*
  | Data_Type: *UTF-8 Text*
  
  A free-format text field to note any unusual circumstances.

<sb:Flat_Field>
==================================
| **Cardinality:** *Optional*
| **XPath:** *<./sb:Calibration_Reference_Files/sb:Flat_Field>*

The sb:Flat_Field class identifies the PDS archive product containing the 
flat field used to calibrate the data in the product.

<sb:file_name>
  | **Cardinality:** *Optional*
  | **Data Type:** ASCII Short String

  The *sb:file_name* attribute contains the name of the flat field file, without
  path information. This is provided for convenience; it is not expected that the
  name will be resolvable without the associated LIDVID within the PDS archive.

<pds:Internal_Reference>
  | **Cardinality:** *Required*
  | **XPath:** *<./sb:Calibration_Reference_Files/sb:Flat_Field/pds:Internal_Reference>*

  This class provides the explicit link to the archived product containing the 
  flat field used to process the data. It must reference that file by both 
  logical identifier and version (i.e., by "LIDVID"). 

  The *pds:reference_type* attribute must have the value **image_to_flat_field_file**.

<sb:Dark_Field>
==================================
| **Cardinality:** *Optional*
| **XPath:** **XPath:** *<./sb:Calibration_Reference_Files/sb:Dark_Field>*

The sb:Dark_Field class identifies the PDS archive product containing the 
dark field used to calibrate the data in the product.

<sb:file_name>
  | **Cardinality:** *Optional*
  | **Data Type:** ASCII Short String

  The *sb:file_name* attribute contains the name of the dark field file, without
  path information. This is provided for convenience; it is not expected that the
  name will be resolvable without the associated LIDVID within the PDS archive.

<pds:Internal_Reference>
  | **Cardinality:** *Required*
  | **XPath:** *<./sb:Calibration_Reference_Files/sb:Dark_Field/pds:Internal_Reference>*

  This class provides the explicit link to the archived product containing the 
  dark field used to process the data. It must reference that file by both 
  logical identifier and version (i.e., by "LIDVID"). 

  The *pds:reference_type* attribute must have the value **image_to_dark_field_file**.

<sb:Bias_Map>
==================================
| **Cardinality:** *Optional*
| **XPath:** **XPath:** *<./sb:Calibration_Reference_Files/sb:Bias_Map>*

The *sb:Bias_Map* class identifies the PDS archive product containing the 
pixel-by-pixel bias values used to calibrate the data in the product.

<sb:file_name>
  | **Cardinality:** *Optional*
  | **Data Type:** ASCII Short String

  The *sb:file_name* attribute contains the name of the bias map file, without
  path information. This is provided for convenience; it is not expected that the
  name will be resolvable without the associated LIDVID within the PDS archive.

<pds:Internal_Reference>
  | **Cardinality:** *Required*
  | **XPath:** *<./sb:Calibration_Reference_Files/sb:Bias_Map/pds:Internal_Reference>*

  This class provides the explicit link to the archived product containing the 
  bias map used to process the data. It must reference that file by both 
  logical identifier and version (i.e., by "LIDVID"). 

  The *pds:reference_type* attribute must have the value **image_to_bias_levels**.

<sb:Bad_Pixel_Map>
==================================
| **Cardinality:** *Optional*
| **XPath:** **XPath:** *<./sb:Calibration_Reference_Files/sb:Bias_Map>*

The *sb:Bad_Pixel_Map* class identifies the PDS archive product containing the 
bad pixel map used to calibrate the data in the product.

<sb:file_name>
  | **Cardinality:** *Optional*
  | **Data Type:** ASCII Short String

  The *sb:file_name* attribute contains the name of the bad pixel map file, without
  path information. This is provided for convenience; it is not expected that the
  name will be resolvable without the associated LIDVID within the PDS archive.

<pds:Internal_Reference>
  | **Cardinality:** *Required*
  | **XPath:** *<./sb:Calibration_Reference_Files/sb:Bias_Map/pds:Internal_Reference>*

  This class provides the explicit link to the archived product containing the 
  bad pixel map used to process the data. It must reference that file by both 
  logical identifier and version (i.e., by "LIDVID"). 

  The *pds:reference_type* attribute must have the value **image_to_bad_pixel_map**/.


