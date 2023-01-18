# &lt;SB_Metadata&gt; 
**REQUIRED**

The *SBS_Metadata* class provides metadata
        specific to the techniques and processes of small bodies
        research. In some cases the metadata is supplemental to more
        general metadata contained in other namespaces (metadata that
        should also be present in the product label).

## &lt;Observation_Parameters&gt; 
**OPTIONAL**

The *sb:Observational_Parameters* class provides
general attributes that small bodies researches find useful for
a variety of types of observations. Not all subclasses will be
applicable to all data types. The *sb:Filter* subclass may be
repeated, but note that if this is a spectral observation, the
relevant filter characteristics must be included the Spectral
Dictionary (sp:). Additional filter information may be provided
here if desired, of course.
        
### &lt;Exposure&gt;
**OPTIONAL**

  The *sb:Exposure* class is used to provide
        attributes describing what constitutes an "exposure" in the
        particular circumstances of the observation. It is used
        primarily with non-imaging data, or imaging data that does not
        fit the circumstances covered by the Imaging namespace. The
        Imaging namespace class should be used when it is applicable.
        This class may be used in addition to the Imaging class in order
        to provide additional detail via the sb:exposure_description
        attribute.
        
#### &lt;exposure_duration&gt;
**OPTIONAL**

As in the Imaging namespace, *sb:exposure_duration*
        indicates the total time a detector was exposed to or gathering
        a "signal". This element is used in cases where non-standard
        imaging techniques (those not described by the Imaging
        dictionary) are used, or when the detector is detecting
        something other than photons.

#### &lt;exposure_description
**OPTIONAL**

The *sb:exposure_description* attribute should be
        used, typically in conjunction with the exposure_duration
        attribute, when the data collection process involves something
        other than simple photon collection over a continuous period of
        time. The exposure_description should define what constitutes as
        "exposure", and/or how the "duration" is determined.
        
### &lt;Filter&gt;
**OPTIONAL, Repeatable**

The *sb:Filter* class provides local and standard
        identification of the filter used to make the observation, as
        well as descriptive parameters to identify types of filter
        (broadband, LVF, etc.) and basic filter characteristics
        (bandpass, center wavelegth).
        
#### &lt;filter_name&gt;        
**REQUIRED**

The *sb:filter_name* is a (frequently informal)
        identifier for the filter within the context of the source data
        collection. Typical values will be things like "Red", "Clear",
        or "CH4". Values should be simple ASCII strings.
        
#### &lt;standard_filter_identification&gt;     
**OPTIONAL**

The *sb:standard_filter_identification* is used when
        the filter is one of a standard or well-known bandpass, for
        example "Johnson V" or "WFPC2 R".
        
#### &lt;filter_type&gt;        
**REQUIRED**

The *sb:filter_type* attribute is a broad
        categorization of the nature of the pass band. Permissible
        values are defined as they are needed - contact the SB Steward
        for assistance.
        
Current permissible values are:
- **Clear** 
- **Broadband**
- **Narrowband**
- **Linear Variable Filter (LVF)**
        
#### &lt;center_wavelength&gt;        
**OPTIONAL**

The *sb:center_wavelength* attribute defines the
        nominal transmission peak of the filter transmission curve,
        assuming the spectral response is a Gaussian function.
        
#### &lt;center_Wavelength_is_weighted&gt;        
**OPTIONAL**

If the preceding center_wavelength is actually
        a weighted center wavelength (rather then the peak of a nominal
        Gaussian function), then this attribute should be present with a
        value of "true". The attribute should never appear without the
        center_wavelength attribute.
        
#### &lt;short_wavelength_limit&gt;        
**OPTIONAL**

The *sb:short_wavelength_limit* defines the smallest
        wavelength cutoff of a wavelength range.
        
#### &lt;long_wavelength_limit&gt;        
**OPTIONAL**

The *sb:long_wavelength_limit* defines the largest
        wavelength cutoff of a wavelength range.
        
#### &lt;known_short_wavelength_leak&gt;        
**OPTIONAL**

If the filter in use has a known light leak on
        the short-wavelength side, the *sb:known_short_wavelength_leak* flag
        should be present and set to "true". This does NOT indicate that
        a correction has been applied - check the calibration processing
        for that information.
        
#### &lt;known_long_wavelength_leak&gt;        
**OPTIONAL**

If the filter in use has a known light leak on
        the long-wavelength side, the *sb:known_long_wavelength_leak* flag
        should be present and set to "true". This does NOT indicate that
        a correction has been applied - check the calibration processing
        for that information.
        
#### &lt;comment&gt;        
**OPTIONAL**

The *sb:comment* is a place to note any unusual circumstances related to the filter.
        
#### &lt;pds:Internal_Reference&gt;        
**OPTIONAL, Repeatable**

This class from the pds: namespace may be included here to link to documents in the 
archive specific to the filter - for example, a filter transmission curve. It may 
be repeated if there are multiple such documents.

The *pds:reference_type* attribute in this class must have one of these values:
- data_to_filter_transmission_curve
- data_to_filter_description

### &lt;Timing&gt;
**OPTIONAL**

The *sb:Timing* class provides additional time
        specifications related to the observation. These might include
        times of particular interest, or alternate formats (Julian date,
        for example) of times expressed in ISO standard formats
        elsewhere. The *sb:comment* field should be used to explain any
        unusual or potentially ambiguous circumstances.
        
#### &lt;midobservation_time_UTC_YMD&gt:
**OPTIONAL**

The *sb:midobservation_time_UTC_YMD* attribute
        contains the UTC time corresponding the midpoint of the
        observation, in the format YYYY-MM-DDThh:mm:ss.sssZ (that is,
        the ISO YMD format with the 'Z' timezone indicator required to
        be present). Unusual circumstances relating to the definition of
        "midobservation" should be explained briefly in the *sb:comment*
        field of the containing class.
        
#### &lt;midobservation_time_UTC_JD&gt:
**OPTIONAL**

The *sb:midobservation_time_UTC_JD* attribute
        contains the UTC time corresponding to the midpoint of the
        observation, in full (as opposed to modified) Julian date
        format. The unit of "julian day" must be included when this
        attribute is used. Unusual circumstances relating to the
        definition of "midobservation" should be explained briefly in
        the *sb:comment* field of the containing class.
        
#### &lt;start_time_UTC_JD&gt:
**OPTIONAL**

The *sb:start_time_UTC_JD* attribute contains the
        UTC start time of a period of interest, typically the
        observation period, expressed as a Julian date. Units of "julian
        day" must be included when using this attribute.
        
#### &lt;stop_time_UTC_JD&gt:
**OPTIONAL**

The *sb:stop_time_UTC_JD* attribute contains the UTC
        ending time of a period of interest, typically the observation
        period, expressed as a Julian date. Units of "julian day" must
        be included when using this attribute.
        
#### &lt;comment&gt:
**OPTIONAL**

A free-text comment field for explaining any unusual circumstances.
        
## &lt;Additional_Image_Metadata&gt;
**OPTIONAL**

The *sb:Additional_Image_Metadata* class provides
        metadata to supplement the standard image metadata supplied by
        the more general discipline classes. The *sb:comment* field may be
        used to note any unsual circumstances.
        
### &lt;pds:Local_Internal_Reference&gt;
**REQUIRED**

This class is used tie the metadata of the *sb:Additional_Image_Metadata* class to a specific
image object in this product.

The value of *pds:local_reference_type* must be:
- image_to_additional_metadata

### &lt;comment&gt;
**OPTIONAL**  

Use this free-text comment field to note any unusual circumstances.

### &lt;image_observation_type&gt;
**REQUIRED**        

The *sb:image_observation_type* attribute indicates whether the data product
      is a single, 2D image, or an image "frame sequence" - a series of images 
      obtained in a single observing sequence and processed as a set. If the images
      were intended to comprise a spectral cube or an movie sequence, then the data
      should be labeled accordingly and this class may not be present if there is 
      no additional metadata needed. Additional types can be added to the permissible
      value list as needs arise. When in doubt, check with the PDS node curating the 
      data or raise an issue on this dictionary.
      
Current permissible values for this attribute are:
- Frame Sequence
- Single Image

### &lt;Ancillary_Data_Objects&gt;
**OPTIONAL**        

The *sb:Ancillary_Data_Objects* class provides
        mappings between the primary image data in the product and the
        ancillary data (quality maps, error estimates, etc.) provided
        with it as part of the data product. The optional *sb:comment*
        field may be used to note any unusual circumstances.
        
#### &lt;comment&gt;
**OPTIONAL**

A free-form text field for noting unusual circumstances.
        
#### &lt;Quality_Map&gt;
**OPTIONAL**

The *sb:Quality_Map* class links the primary
        image data in the product to the data object (within the same
        product) containing the pixel-for-pixel quality assessment
        information. It also provides the definitions associated with
        the quality values. The optional *sb:comment* field may be used to
        note any unusual circumstances.
        
##### &lt;pds:Local_Internal_Reference&gt;
**REQUIRED**

This class is used to link to the data object in the product that contains
the quality map for the image data.

The *pds:local_reference_type* must have this value:
- image_to_quality_map
        
##### &lt;Quality_Map_Definition&gt;
**REQUIRED**

The *sb:Quality_Map_Definition* class defines
        attributes related to a "Quality Map" data structure - that is,
        an array with dimensions corresponding to the primary data array
        that contains pixel-for-pixel quality information for every
        pixel in the primary array. *sb:Quality_Map_Defintion* lists the
        meaning of each quality values used in the map. Note that flag
        values defined for the Quality Map should not be used to replace
        *pds:Special_Constants* values - in particular the
        *pds:missing_constant* value - that should be included in the
        defintion of either the primary data array or the Quality Map
        array itself. The *pds:Special_Constants* class is used for
        visualization and data validation; the quality values defined
        are used for interpretation and analysis.
        
*sb:Quality_Map* structure:
- &lt;sb:flags_are_bit_flags&gt;
  
  **REQUIRED**
   
   The *sb:flag_are_bit_flags* attribute contains
        "true" if the flags being defined within the containing class
        correspond to specific bits within a single integer field. When
        this is the case, all flag should have values that are exponents
        of 2. Typically, when bit flags are used, several flags may be
        combined within a single field (so a quality value may be 10,
        indicating that the flags corresponding to the values 8 and 2
        are both set, for example).
- &lt;sb:best_quality_value&gt;
  
  **REQUIRED**

  The *sb:best_quality_value* attribute provides
        the value used within a quality map to indicate the best quality
        pixels. When bit flags are in use, for example, the "best"
        quality is typically 0 (zero) - that is, no quality issues are
        flagged at all.
- &lt;Quality_Flag_Definition&gt;
  
  **REQUIRED, Repeatable**
  
  The *sb:Quality_Flag_Definition* class defines
        one flag value with its corresponding meaning within a
        *sb:Quality_Map_Definition* class. Note that flag values here
        should not be used to replace *pds:Special_Constants* values - in
        particular the *pds:missing_constant* value - that should be
        included in the defintion of the data array itself. The
        *pds:Special_Constants* class is used for visualization and data
        validation; the *sb:Quality_Flag_Definition*s are used for
        interpretation and analysis.
  - &lt;flag_value&gt;
    
    **REQUIRED**
    
    The *sb:flag_value* attribute defines an integer
        value that corresponds to a specific condition or assessment
        within the containing data structure, typically a quality map.
  - &lt;flag_meaning&gt;
    
    **REQUIRED**
    
    The *sb:flag_meaning* attribute defines the
        significance of the particular value when it occurs in the
        associated context (typically a quality map, for example).
        
##### &lt;comment&gt;
**OPTIONAL**

A free-form text field for noting unusual circumstances.
        
#### &lt;Error_Estimates_Map&gt;
**OPTIONAL**

The *sb:Error_Estimates_Map* class links the
        primary image data in the product to the data object (within the
        same product) containing the pixel-for-pixel error estimates.
        The definition of the data object itself should indicate the
        unit of measure of the errors and related information. The
        optional *sb:comment* in this class can be used to note any
        unusual circumstances not related to reading (that is,
        input/output of) the error map data.
        
##### &lt;pds:Local_Internal_Reference&gt;
**REQUIRED**

This class is used to link to the data object in this product containing the
error estimates corresponding to the pixels of the image data.

The *pds:local_reference_type* must be:
- image_to_error_map

##### &lt;comment&gt;

Free-form text to note unusual circumstances.
        
#### &lt;SNR_Map&gt;
**OPTIONAL**

The *sb:SNR_Map* class links the primary image
        data in the product to the data object (within the same product)
        containing the pixel-for-pixel signal-to-noise ratio
        information. The optional *sb:comment* field may be used to note
        any unusual circumstances.
        
##### &lt;pds:Local_Internal_Reference&gt;
**REQUIRED**

This class is used to link to the data object in this product containing the
corresponding signal-to-noise ratio for the pixels of the image data.

The *pds:local_reference_type* must be:
- image_to_snr_map

##### &lt;comment&gt;

Free-form text to note unusual circumstances.

### &lt;Calibration_Applied&gt;
**OPTIONAL**        

The *sb:Calibration_Applied* class provide flags
        to indicate specific calibration processes that have been
        performed, as well as references to files provided with the
        archive that were used as part of the processing. The otpional
        *sb:comment* field may be used to note any unusual circumstances.
        
#### &lt;comment&gt;
**OPTIONAL**

Free-format text to note unusual circumstances
        
#### &lt;bias_subtraction&gt;
**OPTIONAL**

The *sb:bias_subtraction* attribute should be
        present and contain the value "true" if bias subtraction has
        been performed as part of the processing applied to the data
        comprising the product.
        
#### &lt;dark_current_removal&gt;
**OPTIONAL**

The *sb:dark_current_removal* attribute should be
        present and contain the value "true" if dark current removal has
        been performed as part of the processing applied to the data
        comprising the product.
        
#### &lt;flat_field_subtraction&gt;
**OPTIONAL**

The *sb:flat_field_subtraction* attribute should
        be present and contain the value "true" if flat field
        subtraction has been performed as part of the processing applied
        to the data comprising the product.
        
#### &lt;scattered_light_correction&gt;
**OPTIONAL**

The _sb:scattered_light_correction_ attribute
        should be present and contain the value "true" if scattered
        light correction has been applied as part of the processing of
        the data comprising the product.
        
#### &lt;conversion_to_physical_units&gt;
**OPTIONAL**

The _sb:conversion_to_physical_units_ attribute
        should be present and contain the value "true" if the primary
        data is expressed in physical units once any value offset and
        scaling factor included in the definition of the data structure
        have been applied.
        
#### &lt;Calibration_Reference_Files&gt;
**OPTIONAL**

The _sb:Calibration_Reference_Files_ class
        provides explicit references to key calibration files provided
        as part of the archive. Note that these references are required
        to be to specific versions of calibration files, as calibration
        processes and details typically evolve over time. The optional
        _sb:comment_ should be used to note any unusual circumstances
        related to the calibration files as a group. The optional
        _pds:comment_ field in the _pds:Internal_Reference_ class should be
        used to note any unusual circumstances related to any particular
        referenced file.
        
The *sb:Calibration_Reference_Files* class has the following structure:
- &lt;comment&gt;

  **OPTIONAL**
  
  Free-format text for noting unusual circumstances.
  
- &lt;Flat_Field&gt;

  **OPTIONAL**
  
  The _sb:Flat_Field_ class identifies the PDS
        archive product containing the flat field used to calibrate the
        data in the product.
        
  - &lt;file_name&gt;

    **OPTIONAL**
  
    The _sb:file_name_ attribute should contain the
        name, preferably without path information, of the file
        referenced more formally by a _pds:Internal_Reference_ class in
        the same containing class. The file name is provided as a matter
        of convenience and for use as a validation cross-check when the
        data are accepted for archiving. Path information is unlikely to
        be useful once the data are archived, and as the data are
        curated both paths and file names may change. Consequently, the
        logical identifier appearing in the _pds:Internal_Reference_
        should be considered the positive identification of the file in
        question within the archive, rather than the name.
        
  - &lt;pds:Internal_Reference&gt;
  
    **REQUIRED**
    
    This class provides the formal reference to the flat field product.
    
    The *pds:reference_type* must have the value **image_to_flat_field**
    
  - &lt;comment&gt;
  
    **OPTIONAL**
    
    Free-format text to note unusual circumstances
  
- &lt;Dark_Field&gt;

  **OPTIONAL**
  
  The _sb:Dark_Field_ class identifies the PDS
        archive product containing the dark field used to calibrate the
        data in the product.
        
  - &lt;file_name&gt;

    **OPTIONAL**
  
    The _sb:file_name_ attribute should contain the
        name, preferably without path information, of the file
        referenced more formally by a _pds:Internal_Reference_ class in
        the same containing class. The file name is provided as a matter
        of convenience and for use as a validation cross-check when the
        data are accepted for archiving. Path information is unlikely to
        be useful once the data are archived, and as the data are
        curated both paths and file names may change. Consequently, the
        logical identifier appearing in the _pds:Internal_Reference_
        should be considered the positive identification of the file in
        question within the archive, rather than the name.
        
  - &lt;pds:Internal_Reference&gt;
  
    **REQUIRED**
    
    This class provides the formal reference to the flat field product.
    
    The *pds:reference_type* must have the value **image_to_dark_field**
    
  - &lt;comment&gt;
  
    **OPTIONAL**
    
    Free-format text to note unusual circumstances
        
  
- &lt;Bad_Pixel_Map&gt;

  **OPTIONAL**
  
  The _sb:Bad_Pixel_Map_ class identifies the PDS
        archive product containing the bad pixel map applied in
        processing the data in the product.
        
  - &lt;file_name&gt;

    **OPTIONAL**
  
    The _sb:file_name_ attribute should contain the
        name, preferably without path information, of the file
        referenced more formally by a _pds:Internal_Reference_ class in
        the same containing class. The file name is provided as a matter
        of convenience and for use as a validation cross-check when the
        data are accepted for archiving. Path information is unlikely to
        be useful once the data are archived, and as the data are
        curated both paths and file names may change. Consequently, the
        logical identifier appearing in the _pds:Internal_Reference_
        should be considered the positive identification of the file in
        question within the archive, rather than the name.
        
  - &lt;pds:Internal_Reference&gt;
  
    **REQUIRED**
    
    This class provides the formal reference to the flat field product.
    
    The *pds:reference_type* must have the value **image_to_bad_pixel_map**
    
  - &lt;comment&gt;
  
    **OPTIONAL**
    
    Free-format text to note unusual circumstances
        

### &lt;Additional_Geometry_Metadata&gt;
**OPTIONAL**

### &lt;Per_Frame_Metadata&gt;
**OPTIONAL**
