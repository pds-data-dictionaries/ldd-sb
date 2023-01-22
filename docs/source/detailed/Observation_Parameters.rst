<sb:Observation_Parameters>
##################################################

**XPath:** *<sb:SB_Metadata/Observational_Parameters>*

This is one of the main subclasses under the <sb:SB_Metadata> public 
class. It is optional and non-repeatable.

The *sb:Observational_Parameters* class provides
general attributes that small bodies researches find useful for
a variety of types of observations. Not all subclasses will be
applicable to all data types. The *sb:Filter* subclass may be
repeated, but note that if this is a spectral observation, the
relevant filter characteristics must be included the Spectral
Dictionary (sp:). Additional filter information may be provided
here if desired, of course.

The *sb:Observational_Parameters* class contains three main subclasses:

* :ref:`exposure`
* :ref:`filter`
* :ref:`timing`


.. _exposure:

**************************************************
 <sb:Exposure>
**************************************************
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

<sb:exposure_duration>
==================================================

**OPTIONAL**

As in the Imaging namespace, *sb:exposure_duration*
indicates the total time a detector was exposed to or gathering
a "signal". This element is used in cases where non-standard
imaging techniques (those not described by the Imaging
dictionary) are used, or when the detector is detecting
something other than photons.

<sb:exposure_description>
==================================================

**OPTIONAL**

The *sb:exposure_description* attribute should be
used, typically in conjunction with the exposure_duration
attribute, when the data collection process involves something
other than simple photon collection over a continuous period of
time. The exposure_description should define what constitutes as
"exposure", and/or how the "duration" is determined.

.. _filter:

**************************************************
<sb:Filter>
**************************************************
**OPTIONAL, Repeatable**

The *sb:Filter* class provides local and standard
identification of the filter used to make the observation, as
well as descriptive parameters to identify types of filter
(broadband, LVF, etc.) and basic filter characteristics
(bandpass, center wavelegth).

<sb:filter_name>
==================================================

**REQUIRED**

The *sb:filter_name* is a (frequently informal)
identifier for the filter within the context of the source data
collection. Typical values will be things like "Red", "Clear",
or "CH4". Values should be simple ASCII strings.

<sb:standard_filter_identification>     
==================================================

**OPTIONAL**

The *sb:standard_filter_identification* is used when
the filter is one of a standard or well-known bandpass, for
example "Johnson V" or "WFPC2 R".

<sb:filter_type>
==================================================

**REQUIRED**

The *sb:filter_type* attribute is a broad
categorization of the nature of the pass band. Permissible
values are defined as they are needed - contact the SB Steward
for assistance.

Current permissible values are:

* **Clear** 
* **Broadband**
* **Narrowband**
* **Linear Variable Filter (LVF)**

<sb:center_wavelength>
==================================================

**OPTIONAL**

The *sb:center_wavelength* attribute defines the
nominal transmission peak of the filter transmission curve,
assuming the spectral response is a Gaussian function.

<sb:center_Wavelength_is_weighted>
==================================================

**OPTIONAL**

If the preceding center_wavelength is actually
a weighted center wavelength (rather then the peak of a nominal
Gaussian function), then this attribute should be present with a
value of "true". The attribute should never appear without the
center_wavelength attribute.

<sb:short_wavelength_limit>
==================================================

**OPTIONAL**

The *sb:short_wavelength_limit* defines the smallest
wavelength cutoff of a wavelength range.

<sb:long_wavelength_limit>
==================================================

**OPTIONAL**

The *sb:long_wavelength_limit* defines the largest
wavelength cutoff of a wavelength range.

<sb:known_short_wavelength_leak>
==================================================

**OPTIONAL**

If the filter in use has a known light leak on
the short-wavelength side, the *sb:known_short_wavelength_leak* flag
should be present and set to "true". This does NOT indicate that
a correction has been applied - check the calibration processing
for that information.

<sb:known_long_wavelength_leak>
==================================================

**OPTIONAL**

If the filter in use has a known light leak on
the long-wavelength side, the *sb:known_long_wavelength_leak* flag
should be present and set to "true". This does NOT indicate that
a correction has been applied - check the calibration processing
for that information.

<sb:comment>
==================================================

**OPTIONAL**

The *sb:comment* is a place to note any unusual circumstances related to the filter.

<sb:pds:Internal_Reference>
==================================================
**OPTIONAL, Repeatable**

This class from the pds: namespace may be included here to link to documents in the 
archive specific to the filter - for example, a filter transmission curve. It may 
be repeated if there are multiple such documents.

The *pds:reference_type* attribute in this class must have one of these values:

* **data_to_filter_transmission_curve**
* **data_to_filter_description**

.. _timing:

**************************************************
<sb:Timing>
**************************************************

**OPTIONAL**

The *sb:Timing* class provides additional time
specifications related to the observation. These might include
times of particular interest, or alternate formats (Julian date,
for example) of times expressed in ISO standard formats
elsewhere. The *sb:comment* field should be used to explain any
unusual or potentially ambiguous circumstances.

<sb:midobservation_time_UTC_YMD>
==================================================

**OPTIONAL**

The *sb:midobservation_time_UTC_YMD* attribute
contains the UTC time corresponding the midpoint of the
observation, in the format YYYY-MM-DDThh:mm:ss.sssZ (that is,
the ISO YMD format with the 'Z' timezone indicator required to
be present). Unusual circumstances relating to the definition of
"midobservation" should be explained briefly in the *sb:comment*
field of the containing class.

<sb:midobservation_time_UTC_JD>
==================================================

**OPTIONAL**

The *sb:midobservation_time_UTC_JD* attribute
contains the UTC time corresponding to the midpoint of the
observation, in full (as opposed to modified) Julian date
format. The unit of "julian day" must be included when this
attribute is used. Unusual circumstances relating to the
definition of "midobservation" should be explained briefly in
the *sb:comment* field of the containing class.

<sb:start_time_UTC_JD>
==================================================

**OPTIONAL**

The *sb:start_time_UTC_JD* attribute contains the
UTC start time of a period of interest, typically the
observation period, expressed as a Julian date. Units of "julian
day" must be included when using this attribute.

<sb:stop_time_UTC_JD>
==================================================

**OPTIONAL**

The *sb:stop_time_UTC_JD* attribute contains the UTC
ending time of a period of interest, typically the observation
period, expressed as a Julian date. Units of "julian day" must
be included when using this attribute.

<sb:comment>
==================================================

**OPTIONAL**

A free-text comment field for explaining any unusual circumstances.
