# Regression Test Directory

This directory contains the following VALID-only test files:

**SBmetadataTemplate_VALID.xml**

  A psuedo-label that includes every class and attribute in the SB namespace. It does
  not reflect any real situation. It is possibly useful as a design reference.
  
**mc0-Proc_VALID.xml** and **mpf-Proc_VALID.xml**

  Stripped-down labels from New Horizons MVIC migration design mockups. They reflect 
  more realistic usage.
  
Tests for individual key features are provided in VALID/FAIL pairs:

**calfiles_require_lidvids**

  These files demonstrate that the pds:Internal_Reference class in the 
  sb:Calibration_Reference_Files classes require that the PDS4 calibration file 
  products are references by LIDVID and not just LID.
  
**julian_dates_unit_check**

  These files demonstrate that every attribute that is identified as contains a 
  Julian date formatted time (they all have names ending in "_JD") has "julian day"
  as the value of its unit attribute, and not some other valid *Units_of_Time* value.
