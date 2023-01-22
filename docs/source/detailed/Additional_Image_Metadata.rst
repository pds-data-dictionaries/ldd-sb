<sb:Additional_Image_Metadata>
########################################

**XPath:** *<sb:SB_Metadata/sb:Additional_Image_Metadata>*

This is one of the main subclasses under the <sb:SB_Metadata> public 
class. It is optional and not repeatable.

The *sb:Additional_Image_Metadata* class provides
metadata to supplement the standard image metadata supplied by
the more general discipline classes. The *sb:comment* field may be
used to note any unsual circumstances.

The *sb:Additional_Image_Metadata* class contains the following subclasses and attribute:

* :ref:`local-internal-reference`
* :ref:`comment`
* :ref:`image-observation-type`
* :ref:`ancillary-data-objects`
* :ref:`additional-geometry-metadata`
* :ref:`per-frame-metadata`

.. _local-internal-reference:

***********************************************
<pds:Local_Internal_Reference>
***********************************************
**REQUIRED**

This class is used tie the metadata of the *sb:Additional_Image_Metadata* class to a specific
image object in this product.

The value of *pds:local_reference_type* must be **image_to_additional_metadata**.

.. _comment:

***********************************************
<sb:comment>
***********************************************
**OPTIONAL**  

Use this free-text comment field to note any unusual circumstances.

.. _image-observation-type:

***********************************************
<sb:image_observation_type>
***********************************************
**REQUIRED**

The *sb:image_observation_type* attribute indicates whether the data product
is a single 2D image or an image "frame sequence" - a series of images 
obtained in a single observing sequence and processed as a set. If the images
were intended to comprise a spectral cube or an movie sequence, then the data
should be labeled accordingly and this class may not be present if there is 
no additional metadata needed. Additional types can be added to the permissible
value list as needs arise. When in doubt, check with the PDS node curating the 
data or raise an issue on this dictionary.

Current permissible values for this attribute are:
* **Frame Sequence**
* **Single Image**

.. _ancillary-data-objects:

***********************************************
<sb:Ancillary_Data_Objects>
***********************************************
**OPTIONAL**

The *sb:Ancillary_Data_Objects* class provides
mappings between the primary image data in the product and the
ancillary data (quality maps, error estimates, etc.) provided
with it as part of the data product. The optional *sb:comment*
field may be used to note any unusual circumstances.

<sb:comment>
===============================================

**OPTIONAL**

A free-form text field for noting unusual circumstances.

<sb:Quality_Map>
===============================================

**OPTIONAL**

The *sb:Quality_Map* class links the primary
image data in the product to the data object (within the same
product) containing the pixel-for-pixel quality assessment
information. It also provides the definitions associated with
the quality values. The optional *sb:comment* field may be used to
note any unusual circumstances.
 
<pds:Local_Internal_Reference>
------------------------------------------------

**REQUIRED**

This class is used to link to the data object in the product that contains
the quality map for the image data.

The *pds:local_reference_type* must have the value **image_to_quality_map**.

<sb:Quality_Map_Definition>
------------------------------------------------

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


<sb:flags_are_bit_flags>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**REQUIRED**
   
The *sb:flag_are_bit_flags* attribute contains
"true" if the flags being defined within the containing class
correspond to specific bits within a single integer field. When
this is the case, all flag should have values that are exponents
of 2. Typically, when bit flags are used, several flags may be
combined within a single field (so a quality value may be 10,
indicating that the flags corresponding to the values 8 and 2
are both set, for example).

<sb:best_quality_value>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**REQUIRED**

The *sb:best_quality_value* attribute provides
the value used within a quality map to indicate the best quality
pixels. When bit flags are in use, for example, the "best"
quality is typically 0 (zero) - that is, no quality issues are
flagged at all.

<sb:Quality_Flag_Definition>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**REQUIRED, Repeatable**
  
The *sb:Quality_Flag_Definition* class defines
one flag value with its corresponding meaning within a
*sb:Quality_Map_Definition* class. Note that flag values here
should not be used to replace *pds:Special_Constants* values - in
particular the *pds:missing_constant* value - that should be
included in the definition of the data array itself. The
*pds:Special_Constants* class is used for visualization and data
validation; the *sb:Quality_Flag_Definition*\s are used for
interpretation and analysis.

<sb:flag_value>
""""""""""""""""""""""""""""""""""""""""""""

**REQUIRED**
    
The *sb:flag_value* attribute defines an integer
value that corresponds to a specific condition or assessment
within the containing data structure, typically a quality map.

<sb:flag_meaning>
""""""""""""""""""""""""""""""""""""""""""""

**REQUIRED**
    
The *sb:flag_meaning* attribute defines the
significance of the particular value when it occurs in the
associated context (typically a quality map, for example).

<sb:comment>
--------------------------------------------

**OPTIONAL**

A free-form text field for noting unusual circumstances.

<sb:Error_Estimates_Map>
============================================

**OPTIONAL**

The *sb:Error_Estimates_Map* class links the
primary image data in the product to the data object (within the
same product) containing the pixel-for-pixel error estimates.
The definition of the data object itself should indicate the
unit of measure of the errors and related information. The
optional *sb:comment* in this class can be used to note any
unusual circumstances not related to reading (that is,
input/output of) the error map data.

<pds:Local_Internal_Reference>
--------------------------------------------------

**REQUIRED**

This class is used to link to the data object in this product containing the
error estimates corresponding to the pixels of the image data.

The *pds:local_reference_type* must be **image_to_error_map**.

<sb:comment>
--------------------------------------------------

**OPTIONAL**

Free-form text to note unusual circumstances.

<sb:SNR_Map>
==================================================

**OPTIONAL**

The *sb:SNR_Map* class links the primary image
data in the product to the data object (within the same product)
containing the pixel-for-pixel signal-to-noise ratio
information. The optional *sb:comment* field may be used to note
any unusual circumstances.

<pds:Local_Internal_Reference>
--------------------------------------------------

**REQUIRED**

This class is used to link to the data object in this product containing the
corresponding signal-to-noise ratio for the pixels of the image data.

The *pds:local_reference_type* must be **image_to_snr_map**.

<sb:comment>
--------------------------------------------------

**OPTIONAL**

Free-form text to note unusual circumstances.



.. _additional-geometry-metadata:

**************************************************
<sb:Additional_Geometry_Metadata>
**************************************************
**OPTIONAL**

The *sb:Additional_Geometry_Metadata* class provides information to supplement that
already provided in the classes of the Geometry (geom:) namespace. This class is
only useful in relatively simple cases where there is just a single *geom:Geometry* 
class the label, with a single target and orbiter reference. The optional 
*sb:comment* attribute may be used to note unusual circumstances.

<sb:comment>
==================================================

**OPTIONAL**

Free-form text for noting any unusual circumstances.

<sb:Instrument_Position_Angles>
==================================================

**OPTIONAL**

The *sb:Instrument_Position_Angles* class provide position angles for the
axes of the boresight on the place of the image, measured with respect 
to the location of the celestial North pole (also projected onto the plane
of the image).

<sb:y_axis_position_angle>
--------------------------------------------------

**OPTIONAL**

The *sb:y_axis_position_angle* provides the angle measured East from celestial North
in the plane of an image to the +Y axis of the instrument boresight. The values
are in the range 0-360 degrees.

<sb:z_axis_position_angle>
--------------------------------------------------

**OPTIONAL**

The *sb:z_axis_position_angle* provides the angle measured East from celestial North
in the plane of an image to the +Z axis of the instrument boresight. The values
are in the range 0-360 degrees.

<sb:Geometry_Vector_Time>
==================================================

**OPTIONAL**

The *sb:Geometry_Vector_Time* class identifies a vector or pair of related vectors 
included in the geom:Geometry_Orbiter class and provides details about the local
time for an observer located at one of the endpoints of the vector at the time 
for which the vector was calculated. For example, if the 
*geom:Vector_Cartesian_Position_Earth_to_Target* vector was calculated for 
spacecraft UTC time *X*, this class can be used to provide the additional information
that the UTC time for an Earth Observer at that instant would have been time*Y*.

<sb:position_velocity_vectors>
--------------------------------------------------

**REQUIRED**

The *sb:position_velocity_vectors* attribute identifies the type of position and
velocity vectors relevant to the data provided by naming the start and end point
pair. (In some cases the directionality of the velocity vector is opposite that
of the position vector.)


<sb:time_at_Earth_UTC_YMD>, <sb:time_at_Earth_UTC_JD>, <sb:time_at_Sun_UTC_YMD>, <sb:time_at_Sun_UTC_JD>, <sb:time_at_target_UTC_YMD>, sb:time_at_target_UTC_JD>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**OPTIONAL**

The *sb:time_at_[location]* vectors provide the UTC time in either YMD format or Julian date format for
an observer at the indicated location.

.. _per-frame-metadata:

**************************************************
<sb:Per_Frame_Metadata>
**************************************************
**OPTIONAL**

The *sb:Per_Frame_Metadata* class provides timing and pointing information specific
to a single, specified frame within a "Frame Sequence" observation. It should not
be used in the case of single-image observations. For single images, the full
*geom:Image_Display_Geometry* class should be used.

<sb:frame_number>
==================================================

**REQUIRED**

The *sb:frame_number* attribute specifies the sequential frame number, starting with
"0", to which the subsequent frame-specific metadata applies. The frame number 
is the subscript along the axis that defines the "frame" dimension. Frames must
be physically stored in sequence in the file, so for a sequence of 2D frames the
sb:frame_number will correspond to the (0-based) index along the third axis.


<sb:frame_exposure_duration>
==================================================

**OPTIONAL**

The *sb:frame_exposure_duration* attribute provides the exposure time for one
frame of a framing sequence.

<sb:comment>
==================================================

**OPTIONAL**

Free-format text field to note unusual circumstances.

<sb:Midframe_Time>
==================================================

**OPTIONAL**

The *sb:Midframe_Time* class provides timing information related to the mid-exposure 
time of one frame of a "Frame Sequence" observation.

<sb:midobservation_time_UTC_YMD>
--------------------------------------------------

**OPTIONAL**

The *sb:midobservation_time_UTC_YMD* attribute contains the UTC time corresponding
the midpoint of the observation, in the format YYYY-MM-DDThh:mm:ss.sssZ
(that is, the ISO YMD format with the 'Z' timezone indicator required to be
present). Unusual circumstances relating to the definition of "midobservation" 
should be explained briefly in the sb:comment field of the containing class.


<sb:midobservation_time_UTC_JD>
--------------------------------------------------

**OPTIONAL**

The *sb:midobservation_time_UTC_JD* attribute contains the UTC time corresponding
to the midpoint of the observation, in full (as opposed to modified) Julian 
date format. The unit of "julian day" must be included when this attribute
is used. Unusual circumstances relating to the definition of "midobservation" 
should be explained briefly in the *sb:comment* field of the containing class.

<sb:delta_time_from_sequence_start>
--------------------------------------------------

**OPTIONAL**

The *sb:delta_time_from_sequence_start* attribute provide the offset of a time of
interest in the current frame (as indicated by the containing class) from the 
start of the sequence in a "Frame Sequence" observation. It is specified
as a floating point number of the specified units of time.


<sb:Frame_Pointing>
==================================================

**OPTIONAL**

The *sb:Frame_Pointing* class provide pointing information specific to one frame
in a "Frame Sequence" observation.

<sb:frame_center_ra>
--------------------------------------------------

**OPTIONAL**

The *sb:frame_center_ra* attribute provide the right ascension, in degrees, of the
center point of a single frame of a "Frame Sequence" observation.


<sb:frame_center_dec>
--------------------------------------------------

**OPTIONAL**

The *sb:frame_center_dec* attribute provide the declination, in degrees, of the
center point of a single frame of a "Frame Sequence" observation.

<sb:celestial_north_clock_angle>
--------------------------------------------------

**OPTIONAL**

The *sb:celestial_north_clock_angle* attribute is the angle, measured clockwise from
"up" to the direction of the celestial north pole. It must be in the range 0-360, 
calculated with respect to the image display as indicated in the corresponding
disp:Display_Settings_Class.

<sb:Instrument_Position_Angles>
--------------------------------------------------

**OPTIONAL**

The *sb:Instrument_Position_Angles* class provide position angles for the
axes of the boresight on the place of the image, measured with respect 
to the location of the celestial North pole (also projected onto the plane
of the image).

<sb:y_axis_position_angle>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**REQUIRED**

The *sb:y_axis_position_angle* provides the angle measured East from celestial North
in the plane of an image to the +Y axis of the instrument boresight. The values
are in the range 0-360 degrees.

<sb:z_axis_position_angle>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**REQUIRED**

The *sb:z_axis_position_angle* provides the angle measured East from celestial North
in the plane of an image to the +Z axis of the instrument boresight. The values
are in the range 0-360 degrees.

<sb:Instrument_to_J2000_Quaternion>
==================================================

**OPTIONAL**

The *sb:Instrument_to_J2000_Quaternion* is provides the quaterion to rotate from
coordinates from the intrument frame to the EME J2000 frame for a single specific
frame of a "Frame Sequence" observation.

<sb:qcos>
--------------------------------------------------

**REQUIRED**

The *sb:qcos* attribute is the "cos(theta/2)" element of a pointing quaternion.

<sb:qsin1>, <sb:qsin2>, <sb:qsin3>
--------------------------------------------------

**REQUIRED**

The *sb:qsin1*, *sb:qsin2*, and *sb:qsin3* attributes are the **ax\*sin(theta/2)**, **ay\*sin(theta/2)**,
and **az\*sin(theta/2)** components of the pointing quaternion, respectively.