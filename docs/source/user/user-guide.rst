.. 2023-01-27, by Anne Raugh

##################################################
Introduction
##################################################

This *User's Guide* provides a brief overview of the Small Bodies (SB or "sb:") namespace
for those designing labels for small bodies data, or those developing code to read 
small bodies data, in the PDS archive. It presents the major features of the namespace 
and typical usage scenarios.


################################################################
Overview of the Small Bodies (SB) Discipline Dictionary
################################################################

.. include:: ../intro.md

- **Steward:** Anne Raugh, Small Bodies Node, University of Maryland (@acraugh on Github)
- **Dictionary Repo:** https://github.com/pds-data-dictionaries/ldd-sb
- **Namespace Prefix:** sb:

Corrections, changes, and additions should be submitted through 
the `PDS LDD Issue Repo <https://github.com/pds-data-dictionaries/PDS4-LDD-Issue-Repo>`_.

##################################################
Organization of Classes and Attributes
##################################################

The Small Bodies dictionary has a single top-level class that must be
used to access any of the SB metadata classes. Below that, there are
major subclasses for specific types of metadata that might be needed
in various cases, depending on the nature and organization of the data.
Small bodies research often involved pulling data together from a wide
range of sources. Consequently, the Small Bodies dictionary classes
are concerned with gathering the specific details and characteristics 
of the observation into label attributes that support discoverability 
across observing platforms and instrumentation and documentation of the 
standard data reduction applied.

The following sections describe the major divisions of the Small Bodies
namespace.

**************************************************
Top-Level Class: <sb:SB_Metadata>
**************************************************

The *SB_Metadata* class acts as a wrapper for all other SB classes. It
is required if you plan to use any SB classes in your label. It contains
the major subclasses of the dictionary. All subclasses are optional;
which classes to use depends on the particular circumstances of the data
being described. The Small Bodies Node (SBN) will be happy to assist in
selecting classes - contact the namespace steward listed above with questions
or requests.

There are three major subclasses in the <sb:SB_Metadata> class:

- :ref:`<sb:Observation_Parameters><observation-parameters>`
- :ref:`<sb:Calibration_Information><calibration-information>`
- :ref:`<sb:Additional_Image_Metadata><additional-image-metadata>`

You can see a complete outline of the namespace under the 
:doc:`../detailed/outline` topic.

.. _observation-parameters:

**************************************************
Main Subclass: <sb:Observation_Parameters>
**************************************************

The *<sb:Observation_Parameters>* class provides additional details to augment information
that is expected to be provided elsewhere in the label. It contains three subclasses:

- <sb:Exposure>
- <sb:Filter>
- <sb:Timing>

The <sb:Observation_Parameters> class is not repeatable. The information provided is
relevant to the observation as a whole, even when the observation consists of a 
series of recorded events.

<sb:Exposure>
  The *<sb:Exposure>* subclass augments the *<img:Exposure>* class from the Imaging
  dictionary. It is used primarily to provide a description field 
  (*<sb:exposure_description>*) to note any unusual Circumstances with respect to 
  how "exposure" is defined for the data product in hand. An *<sb:exposure_duration>*
  attribute is provided, if the user wishes to repeat the duration either in a different
  unit, or for convenience of reference. Note that the *<img:Exposure>* class provides
  attributes for describing exposure-related parameters apart from a free-text 
  description that should be used as applicable in all data labels.
  
  The *<sb:Exposure>* class is optional and not repeatable.

<sb:Filter>
  The *<sb:Filter>* subclass includes specific attributes for describing the various 
  types of filters used in small bodies research. The information here augments 
  both the *<wavelength_range>* information that should be provided in the high-level
  *<Primary_Result_Summar>y* class in the core namespace, as well as the *<img:Filter>*
  class provided in the Imaging namespace. Small bodies researchers use a variety of
  filters that are specialized in various ways to extract specific spectral markers
  or generalized spectral signatures. This class provides attributes to support 
  discoverability based on those characteristics.

  For example, this class is where you can specify that a filter is broadband, narrowband,
  polarizing, etc. The class includes explicit wavelength ranges to cover the cases of 
  filters not well-described by central wavelength and full width at half-maximum. It
  also provides a flag to indicate when the "central wavelength" reported is a weighted
  central wavelength, as opposed to the midpoint of the passband. This
  is also where it is possible to note that a filter has a standard profile (like 
  "Johnson U"), or to link a filter to its documentation (a transmission curve, for
  example), or include the nickname for well-known filters on space telescopes, remote 
  sensing missions, and used in ground-based observing campaigns.
  
  The *<sb:Filter>* class is optional and not repeatable at present.
  
<sb:Timing>
  The *<sb:Timing>* class provides attributes to augment the start and stop times noted
  in the *<Observation_Area>* of the label. It includes an attribute for providing the 
  UTC midobservation time and attributes for the Julian date equivalents of start,
  stop, and midobservation times. It also provides a comment field, for noting any
  unusual circumstances related to timing information in the label.
  
  The *<sb:Timing>* class is optional and note repeatable.

.. _calibration-information:

**************************************************
Main Subclass: <sb:Calibration_Information>
**************************************************

The *<sb:Calibration_Information>* class is primarily concerned with providing provenance
and reproducibility for the basic data reduction processing applied to the data. It does
this in a format that corresponds to the typical, largely source-agnostic, processes used 
in the small bodies community to reduce observational raw data to a form ready for further
analysis.

**It is important to note** that, in PDS4, *calibrated* means "data converted to physical
units". Anything above "raw" but short of "physical units" is *partially processed*. It 
is common to hear researchers refer to data as "calibrated" that is only *partially 
processed* in PDS4 parlance, and to refer to the process of data reduction as "calibration"
irrespective of whether or not it results in data that is *calibrated* by the PDS4 
definition. 
  
Consequently, the word "calibration" is used in the class and attribute names here in
the aspirational sense - the particular steps applied are necessary, but possibly not 
sufficient, to earn the official PDS4 label *calibrated*. This is a case where the dictionary 
terminology reflects the usage within the discipline, rather than the strict definitions
used in the PDS4 archive classifications.

*<sb:Calibration_Information>* has three subclasses:

- <sb:Raw_Data_Product>
- <sb:Calibration_Applied>
- <sb:Calibration_Reference_Files>

The *<sb:Calibration_Information>* class is optional and not repeatable. The processes
described are applicable to the observational data as a whole. While optional, it is 
strongly recommended that this class and all its subclasses be included in all applicable
data specifically targeting small bodies, to support interoperability.

**Note:** A calibration/processing description document should always be part of the archive 
and a link to that document should be included in the high-level *<Reference_List>* class
whenever processed data at any level above "Raw" (and sometimes even then) are archived.

<sb:Raw_Data_Product>
  The *<sb:Raw_Data_Product>* class provides a link to the original source for the present
  processed data product, also in the PDS archives. It includes a place for the file name.
  Although file names should not be considered unique and immutable, they are often 
  referenced in archive documentation and including it can answer a lot of questions very
  quickly. The raw product should be referenced formally using the (required) 
  *<Internal_Reference>* class (defined in the core *pds:* namespace). This reference should
  should be to a specific version of that product - in other words, referenced by LIDVID
  (logical ID and version) rather than just LID.
  
<sb:Calibration_Applied>
  The *<sb:Calibration_Applied>* class contains a series of boolean attributes that must  
  be included to indicate that a particular calibration step (like bias subtraction or 
  flat fielding) has been applied, and may also be used to indicate that a specific
  correction (correction for scattered light, for example) has *not* been applied. There
  is also a *<sb:comment>* field provided to note unusual circumstances.
  
<sb:Calibration_Reference_Files>
  The *<sb:Calibration_Reference_Files>* class is used to create links between the
  processed data and the specific files used as part of the standard data reduction
  sequence. Classes are provided for key calibration steps - for example, the flat
  field file applied is identified in the *<sb:Flat_Field>* subclasses. The file 
  subclasses all have the same form as the *<sb:Raw_Data_Product>* class: an optional
  *<sb:file_name>* provided largely for convenience; and a formal link to the 
  archival product containing the file via the *<Internal_Reference>* class. As with
  most classes in the SB dictionary, this one also contains a *<sb:comment>* field 
  that can be used to note unusual circumstances.

.. _additional-image-metadata:

**************************************************
Main Subclass: <sb:Additional_Image_Metadata>
**************************************************

The *<sb:Additional_Image_Metadata>* class provides subclasses that support some
common image data organizations for single and multi-frame observations, and to
augment the pointing information supplied in the Geometry classes *<geom:Image_Display_Geometry>*
and *<geom:Geometry_Orbiter>*. It contains four subclasses and two attributes. In
label order these are:

- <pds:Local_Internal_Reference>
- <sb:comment>
- <sb:image_observation_type
- <sb:Ancillary_Data_Objects>
- <sb:Additional_Geometry_Metadata>
- <sb:Per_Frame_Metadata>

The *<sb:Additional_Image_Metadata>* class is optional and not repeatable. It will 
most often be used with processed image data to link the processed image to the 
ancillary data objects containing things like signal-to-noise maps and quality
assessments when provided in arrays that map pixel-to-pixel with the image.

<Local_Internal_Reference>
  This class from the core *pds:* namespace is used to identify the data object 
  within the product that contains the primary image data. Most often this is a
  single 2D image array, but in recent missions there has been a trend to collecting
  frames taken as part of an observing sequence (but not necessarily as a "movie", 
  i.e., with irregular time steps) into a 3D stack of frames.
  
<sb:comment>
  As found frequently in the SB dictionary, this is a free-form text field for noting
  any unusual circumstances of which the user should be aware.
  
<sb:image_observation_type>
  This attribute is used to distinguishe between the more usual **Single Frame** data
  product, which contains a single 2D image, and a **Frame Sequence** data product,
  which conains a stack of images resulting from a single observing sequence.
  
<sb:Ancillary_Data_Objects>
  The *<sb:Ancillary_Data_Objects>* class is used in *partially processed* and
  *calibrated* data products to identify and link the primary image data to ancillary
  data provided in data objects that have identical dimenstions to the primary image
  data object. So, for example, if error estimates for a 2D image are provided as a
  2D array containing error values for each corresponding pixel, the 
  *<sb:Ancillary_Data_Objects>* class will be present with an *<sb:Error_Estimates_Map>*
  subclass identifying the data object contiaining the errors.
  
  The ancillary data types currently supported are:
  
  - Error estimates, through the *<sb:Error_Estimates_Map>* subclass
  - Signal-to-noise ratio, through the *<sb:SNR_Map>* subclass
  - Pixel quality assessments, through the *<sb:Quality_Map>* subclass
  
  The *<sb:Quality_Map>* subclass also contains the *<sb:Quality_Map_Definition>* class,
  which can be used to define the values comprising the quality map pixels.
  
  Ancillary data objects are identified using the *<Local_Internal_Reference>* class
  from the *pds:* core dictionary.
  
  The *<sb:Ancillary_Data_Objects>* class is optional but not repeatable.
  
<sb:Additional_Geometry_Metadata>
  The *<sb:Additional_Geometry_Metadata>* class contains classes for attributes not
  available from the Geometry dictionary, but often desired by small bodies 
  researchers for use in analysis. In addition to an initial *<sb:comment>* field
  for the usual notes, this class contains two subclasses:
  
  - <sb:Instrument_Position_Angles>
  - <sb:Geometry_Vector_Times>
  
  The *<sb:Instrument_Position_Angles>* class supplements the *<geom:Image_Display_Geometry>*
  class by adding position angles for the *y* and *z* axes of the instrument pointing on the
  plane of the image, when displayed according to the directions in the *<disp:Display_Settings>*
  class (which should be present in all image data labels).
  
  The *<sb:Geometry_Vector_Times>* class provides a method for specifying UTC at an observer
  located at one end point of the geometry vectors included in the *<geom:Geometry_Orbiter>*
  class. The specific vector is identified, and the UTC at the point of interest (Sun, Earth,
  spacecraft, or target) can be provided in either YMD format or as a Julian date.
  
  The *<sb:Additional_Geometry_Metadata>* class is optional but not repeatable. In the case
  of **Frame Sequence** data products, the values for the additional geometry metadata should
  be referenced to the midpoint of the observing sequence.

**<sb:Per_Frame_Metadata>**
  The *<sb:Per_Frame_Metadata>* class is used only in the case of products containing
  **Frame Sequence** data in order to supply timing and pointing information for each
  2D frame comprising the primary data object. The class is repeated once for each
  frame.
  
  Individual frames are identified by their sequence number, starting at 0 (zero). In
  addition to providing an exposure duration for the frame, this class contains two
  subclasses:
  
  - <sb:Midframe_Time>
  - <sb:Frame_Pointing>
  
  The *<sb:Midframe_Time>* class provides UTC midobservation time for the single frame in
  both YMD and Julian date format, and also a place for the delta time from the start of
  the observing sequence to the midframe time.
  
  The *<sb:Frame_Pointing>* class contains attributes to hold the center of image right
  ascension and declination, celestial north clock angle, and instrument position angles
  for each image, as well as the instrument-to-J2000 rotation quaternion specific to the 
  frame.
  