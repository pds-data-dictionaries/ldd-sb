# Regression Test Directory

This directory contains regression tests in the form of XML label files:

**SBmetadataTemplate_VALID.xml**

  A psuedo-label that includes every class and attribute in the SB namespace except
  where that would produce a validation error. It does 
  not reflect any real situation. It is possibly useful as a design reference.

**all_position_angle_axes_FAIL** and **duplicated_position_angle_axes_FAIL**

  These files test that in the Instrument_Position_Angles class, exactly two
  different axes (of the set [X, Y, Z]) are present

**calfiles_require_lidvids_VALID** and **calfiles_require_lidvids_FAIL**

  These files demonstrate that the pds:Internal_Reference class in the 
  sb:Calibration_Reference_Files classes require that the PDS4 calibration file 
  products are references by LIDVID and not just LID.
  
**julian_dates_unit_check_VALID** and **julian_date_unit_check_FAIL**

  These files demonstrate that every attribute that is identified as containing a 
  Julian date formatted time (they all have names ending in "_JD") has "julian day"
  as the value of its unit attribute, and not some other valid *Units_of_Time* value.
  
**mc0-Proc_VALID** and **mpf-Proc_VALID**

  Stripped-down labels from New Horizons MVIC migration design mockups. They reflect 
  more realistic usage.
  
Tests for individual key features are provided in VALID/FAIL pairs:
