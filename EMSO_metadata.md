# ERDDAP Metadata Specification #

This document includes a list of all the metadata terms required for a dataset to be EMSO Metadata Specification version. Tests
that are required to consider a dataset harmonized and compatible with EMSO internal standards.

**Version**: 0.1

## Global Attributes ##

The attributes listed in the following table are expected to be included as global attributes in all EMSO-compliant
datasets in ERDDAP. The 'global attribute' column is the name of the attribute. The 'compliance test' column refers the
test mechanism used to ensure that the attribute is compliant with the EMSO standard (to see a list of all implemented
tests go to Implemented tests section). The mandatory column.

| Global Attributes            | Description                             | Compliance test    | Required | 
|------------------------------|-----------------------------------------|--------------------|----------|
| date_created                 | Creation date                           | data_type#str      | true     |
| Conventions                  | conventions used in thd dataset         | data_type#str      | false    |
| institution_edmo_code        | EDMO code of the creator's organization | edmo_code          | true     |
| geospatial_lat_min           | ...                                     | coordinate         | true     |
| geospatial_lat_max           | ...                                     | coordinate         | true     |
| geospatial_lon_min           |                                         | coordinate         | true     |
| geospatial_lon_max           |                                         | coordinate         | true     |
| geospatial_vertical_min      |                                         | depth              | true     |
| geospatial_vertical_max      |                                         | depth              | true     |
| time_coverage_start          |                                         | data_type#datetime | true     |
| time_coverage_end            |                                         | data_type#datetime | true     |
| update_interval              |                                         |                    | true     |
| site_code                    |                                         | emso_site_code     | true     |
| emso_facility                |                                         | emso_facility      | false    |
| source                       |                                         |                    |          |
| platform_code                |                                         |                    | true     |
| wmo_platform_code            |                                         |                    |          |
| data_type                    |                                         |                    |          |
| format_version               |                                         |                    |          |
| network                      |                                         |                    | true     |
| data_mode                    |                                         |                    |          |
| title                        |                                         | data_type#str      | true     |
| summary                      |                                         | data_type#str      | true     |
| keywords                     |                                         |                    |          |
| keywords_vocabulary          |                                         |                    |          |
| project                      |                                         |                    |          |
| QC_indicator                 |                                         |                    |          |
| principal_investigator       |                                         | data_type#str      | true     |
| principal_investigator_email |                                         | email              | true     |
| doi                          |                                         |                    |          |
| license                      |                                         | data_type#str      | true     |

## Variable Attributes ##

The following table contains the attributes required to be compliant with EMSO Metadata Specification.

| Variable Attributes  | Description | Compliance test               | Required |
|----------------------|-------------|-------------------------------|----------|
| long_name            |             | data_type#str                 | true     |
| standard_name        |             | cf_standard_name              | true     |
| units                |             | data_type#str                 | true     |
| comment              |             | data_type#str                 | false    |
| coordinates          |             | coordinate                    | true     |
| ancillary_variables  |             | data_type#str                 | false    |
| _FillValue           |             |                               | false    |
| sdn_parameter_name   |             | data_type#str                 | true     |
| sdn_parameter_urn    |             | sdn_vocab_urn#P01             | true     |
| reference_scale      |             | sdn_vocab_urn#P01             | true     |
| sdn_uom_name         |             | data_type#str                 | true     |
| sdn_uom_urn          |             | sdn_vocab_urn#P06             | true     |
| sensor_model         |             | data_type#str                 | true     |
| sensor_manufacturer  |             | data_type#str                 | true     |
| sensor_reference     |             | data_type#str                 | true     |
| sensor_serial_number |             | data_type#str                 | true     |
| sensor_mount         |             | oceansites_sensor_mount       | true     |
| sensor_orientation   |             | oceansites_sensor_orientation | true     |

## Compliance Tests ##

* **data_type#<type>**: The parameter type is of a certain type. Possible arguments are 'float', 'str', 'int', 'date'
  and 'datetime'
* **edmo_code**: The parameter is an integer number representing an organization listed in
  the  [EDMO database](https://edmo.seadatanet.org/) (European Directory of Marine Organizations).
* **coordinate**: A floating-point number from -90 to +90. 5 digits are required.
* **depth**: The depth value in meters. Positive values indicate positions above sea level.
* **emso_faciliy**: A valid name for an EMSO Regional Facility (EMSO_codes.md)
* **emso_site_code**: A valid name for an EMSO Site Code.
* **email**: valid email
* **oceansites_sensor_orientation**: A valid value from sensor_orientation table (OceanSites_codes.md)
* **oceansites_sensor_mount**: A valid value from sensor_orientation table (OceanSites_codes.md)
* **sdn_vocab_urn#<vocab_id>**: The parameter is a urn in a SeaDataNet vocabulary. Possible values are P01 (parameters),
  P06 (units), L22 (devices), etc. 
