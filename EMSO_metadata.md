# ERDDAP Metadata Specification #

This document includes a list of all the metadata terms required for a dataset to be compliant with the EMSO Metadata
Specifications. The format is based on the 'OceanSITES Data Format reference Manual v1.4', but adapted to the needs
of [EMSO ERIC](https://emso.eu) (European Seafloor and water-column Obseratory) and its federated data service based
on [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap/index.html).

**Version**: 0.1  
**Creation Date** 2023-03-06  
**Last modification** 2023-03-07

## General conventions ##

The following conventions are applied to all attributes in a dataset:

1. When multiple values are required, use a semicolon-separated list, e.g.

```json
{
  "project": "EMSODEV; EMSO-Link; ENVRI-FAIR"
}
```

2. All attribute names are expected to be present, but optional attributes (required=false) may take a nulll string as
   value:

```json
{
  "required_attribute": "very important metadata",
  "optional_attribute": ""
}
```

## Global Attributes ##

The attributes listed in the following table are expected to be included as global attributes in all EMSO-compliant
datasets in ERDDAP. The 'global attribute' column is the name of the attribute. The 'compliance test' column refers the
test mechanism used to ensure that the attribute is compliant with the specifications (to see a list of all implemented
tests go to Implemented tests section). The mandatory column.

| Global Attributes            | Description                                                            | Compliance test      | Required | 
|------------------------------|------------------------------------------------------------------------|----------------------|----------|
| date_created                 | Creation date                                                          | data_type#str        | true     |
| Conventions                  | conventions used in thd dataset                                        | data_type#str        | false    |
| institution_edmo_code        | EDMO code of the creator's organization                                | edmo_code            | true     |
| geospatial_lat_min           | The southernmost latitude, a value between -90 and 90 degrees          | coordinate#latitude  | true     |
| geospatial_lat_max           | The northernmost latitude, a value between -90 and 90 degrees          | coordinate#latitude  | true     |
| geospatial_lon_min           | The westernmost longitude between -180 and 180                         | coordinate#longitude | true     |
| geospatial_lon_max           | The easternmost longitude between -180 and 180                         | coordinate#longitude | true     |
| geospatial_vertical_min      | Minimum depth of measurements in metres (negative for above sea level) | coordinate#depth     | true     |
| geospatial_vertical_max      | Maximum depth of measurements in metres (negative for above sea level) | coordinate#depth     | true     |
| time_coverage_start          | Start date of the data in UTC                                          | data_type#datetime   | true     |
| time_coverage_end            | End date of the data in UTC                                            | data_type#datetime   | true     |
| update_interval              |                                                                        |                      | true     |
| site_code                    |                                                                        | emso_site_code       | true     |
| emso_facility                |                                                                        | emso_facility        | false    |
| source                       |                                                                        | sdn_vocab_name#L06   | false    |
| platform_code                |                                                                        |                      | true     |
| wmo_platform_code            |                                                                        |                      | false    |
| data_type                    |                                                                        |                      | false    |
| format_version               |                                                                        |                      | false    |
| network                      |                                                                        |                      | true     |
| data_mode                    |                                                                        |                      | false    |
| title                        |                                                                        | data_type#str        | true     |
| summary                      |                                                                        | data_type#str        | true     |
| keywords                     |                                                                        |                      | false    |
| keywords_vocabulary          |                                                                        |                      | false    |
| project                      |                                                                        |                      | false    |
| principal_investigator       |                                                                        | data_type#str        | true     |
| principal_investigator_email |                                                                        | email                | true     |
| doi                          |                                                                        |                      | false    |
| license                      |                                                                        | data_type#str        | true     |

## Variable Attributes ##

The following table contains the attributes required to be compliant with EMSO Metadata Specification.

| Variable Attributes  | Description | Compliance test               | Required |
|----------------------|-------------|-------------------------------|----------|
| long_name            |             | data_type#str                 | true     |
| standard_name        |             | cf_standard_name              | true     |
| units                |             | data_type#str                 | true     |
| comment              |             | data_type#str                 | false    |
| coordinates          |             | data_type#str                 | true     |
| ancillary_variables  |             | data_type#str                 | false    |
| _FillValue           |             |                               | false    |
| sdn_parameter_name   |             | data_type#str                 | true     |
| sdn_parameter_urn    |             | sdn_vocab_urn#P01             | true     |
| sdn_uom_name         |             | data_type#str                 | true     |
| sdn_uom_urn          |             | sdn_vocab_urn#P06             | true     |
| sensor_model         |             | data_type#str                 | true     |
| sensor_manufacturer  |             | data_type#str                 | true     |
| sensor_reference     |             | data_type#str                 | true     |
| sensor_serial_number |             | data_type#str                 | true     |
| sensor_mount         |             | oceansites_sensor_mount       | true     |
| sensor_orientation   |             | oceansites_sensor_orientation | true     |

Although the'ancillary_variables' term is not required, it is mandatory to set it in case there is a quality control
column related to the parameter.

## Quality Control Attributes ##

| QC Attributes | Description | Compliance test | Required |
|---------------|-------------|-----------------|----------|
| long_name     |             | data_type#str   | true     |
| conventions   |             | data_type#str   | true     |
| flag_values   |             | data_type#str   | true     |
| flag_meanings |             | data_type#str   | true     |

## Controlled Vocabularies ##

This metadata standard makes use of several controlled vocabularies from
the [NERC Vocabulary Service](https://vocab.nerc.ac.uk)

| vocab ID | description          | URL                                           | 
|----------|----------------------|-----------------------------------------------|
| P01      | parameter vocabulary | [EDMO database](https://edmo.seadatanet.org/) |
| P02      | parameter codes      |                                               |
| P06      | units                |                                               |
| L05      | sensor types         |                                               |
| L06      | platform types       |                                               |
| L22      | sensor models        |                                               |

## Compliance Tests ##

* **data_type#type**: The parameter type is of a certain type. Possible arguments are 'float', 'str', 'int', 'date'
  and 'datetime'
* **edmo_code**: The parameter is an integer number representing an organization listed
  in [EDMO database](https://edmo.seadatanet.org/) (European Directory of Marine Organizations).
* **coordinate#type**: Checks if a coordinate is correct. The 'type' argument must be one of the following: '
  latitude', 'longitude' or 'depths'
* **emso_faciliy**: A valid name for an EMSO Regional Facility (EMSO_codes.md)
* **emso_site_code**: A valid name for an EMSO Site Code.
* **email**: valid email
* **oceansites_sensor_orientation**: A valid value from sensor_orientation table (OceanSites_codes.md)
* **oceansites_sensor_mount**: A valid value from sensor_orientation table (OceanSites_codes.md)
* **sdn_vocab_urn#vocab_id**: The parameter is a urn in a SeaDataNet vocabulary. Possible values are P01 (parameters),
  P02 (parameter codes), P06 (units), L05 (sensor types), L06 platform types) and L22 (sensor models)
  P06 (units), L22 (devices), etc. 
