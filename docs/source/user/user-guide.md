2023-01-22
Anne C. Raugh

# Introduction

This *User's Guide* provides a brief overview of the Small Bodies (SB or "sb:") namespace
for those designing labels for small bodies data, or those developing code to read 
small bodies data, in the PDS archive. 

# Overview of the Small Bodies (SB) Discipline Dictionary

This dictionary contains classes and attributes 
specific to the techniques and processes of small bodies
research. In some cases the metadata provided in the SB dictionary
is specifically identified as supplemental to metadata contained 
in other namespaces - metadata that should also be present in the 
product label.

- **Steward:** Anne Raugh, Small Bodies Node, University of Maryland
- **Dictionary Repo:** https://github.com/pds-data-dictionaries/ldd-sb
- **Namespace Prefix:** sb:

Corrections, changes, and additions should be submitted through the PDS LDD Issue
repo: https://github.com/pds-data-dictionaries/PDS4-LDD-Issue-Repo.

# Organization of Classes and Attributes

The SB dictionary has three major subclasses:

- *[&lt;sb:Observation_Parameters&gt;](../detailed/Observation_Parameters.rst)*
- *[&lt;sb:Calibration_Information&gt;](../detailed/Calibration_Information.rst)*
- *[&lt;sb:Additional_Image_Metadata&gt;](../detailed/Additional_Image_Metadata.rst)*

You can see a complete outline of the namespace under the 
*[Small Bodies Dictionary - Outline](../detailed/outline.rst)* topic, listed under
**DETAILED DOCUMENTATION**. Each of the major subclasses has its own
page providing details of the content of that class.

Every major class is optional. Not all subclasses are needed in all cases.

## &lt;sb:Observation_Parameters&gt;

This class provides details specific to many small bodies observations to augment 
information provided elsewhere in the label regarding exposure details, filter 
characteristics, and Julian date equivalents for key observing times.

## &lt;sb:Calibration_Information&gt;

This class provdes flags to indicate which standard processing for small bodies has been
applied (or not) to the data product, and provides links to calibration files archived
with the data to facility understanding and reproducing the calibration process.

## &lt;sb:Additional_Image_Metadata&gt;

This class provides subclasses to augment the more generally applicable metadata provided
by other discipline namespaces. The primary subclasses are:

- *sb:Ancillary_Data_Objects*, which identifies data objects with a pixel-for-pixel correspondence
  to the image data object that produce ancillary information like error estimate, quality maps,
  signal-to-noise maos, and so on.
- *sb:Additional_Geometry_Metadata*, which provide attributes for time-at-observer corresponding 
  to geometry vectors supplied in the *geom:Geometry_Orbiter* class, position angles in the 
  to field of view to supplement the *geom:Image_Display_Geometry* class, and frame-by-frame
  timing, pointing, and position angle information for observations comprised of a sequence of
  timing framing images not otherwise considered a composite object (like a movie or spectral
  cube observation).

# Detailed Documentation

The **[DETAILED DOCUMENTATION](../detailed/SB_Metadata.md)** for the classes (indicated in the left
menu) provides definitions, permissible values, and 
related information for each class and attribute in the Small Bodies namespace, as well as a pointer
to the namespace outline, which lists all classes and attributes available in label order.

# Examples

This dictionary is in active development. The */test* directory of the repo contains a mock label
that shows the full structure of the namespace, but should not be used as a source of cutting and 
pasting for label design as it is not logically meaningful or complete with respect to the other
discipline namespace that should be present.