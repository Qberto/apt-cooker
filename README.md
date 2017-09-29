# apt-cooker
A process driven by the ArcGIS API for Python to develop, maintain, and manage the FAA's APT Living Atlas layer. 


## About NOTAM Data

### General

AIDAP contains NOTAM and weather data that can be retrieved programmatically, in XML format.  The XML data is retrieved from the Web server using the HTTP POST method.

Note: See the User Guide for the appropriate URLs.

### The Life Cycle of a NOTAM
When a NOTAM is initially stored in the database, the notam_cancel_dtg field is not set, the notam_expire_dtg field is either not set or has some future date and time, and the NOTAM is in active status.  This NOTAM will become inactive when it is cancelled, replaced or it reaches its expiration date and time as specified in notam_expire_dtg.  When a non-FDC NOTAM is cancelled or replaced, both notam_cancel_dtg and notam_delete_dtg fields are set.  When a FDC NOTAM is cancelled, the notam_delete_dtg field is set but the notam_cancel_dtg field is not set for part 1 of the NOTAM.  Therefore, the notam_delete_dtg field is used to identify the active NOTAM.  The inactive NOTAM is retained in the database for a short period before it is deleted from the database.  The notam_lastmod_dtg field will set to current time when the NOTAM is created or modified. 
