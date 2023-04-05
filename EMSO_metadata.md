# ERDDAP Metadata Specification #

This document includes a list of all the metadata terms required for a dataset to be compliant with the EMSO Metadata
Specifications. The format is based on the 'OceanSITES Data Format reference Manual v1.4', but adapted to the needs
of [EMSO ERIC](https://emso.eu) (European Seafloor and water-column Obseratory) and its federated data service based
on [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap/index.html).

**Version**: 0.1
**Creation Date** 2023-03-06  
**Last modification** 2023-04-05

## General conventions ##

The following conventions are applied to all attributes in a dataset:

1. When multiple values are required, use a semicolon-separated list, e.g.

```json
{
  "project": "EMSODEV; EMSO-Link; ENVRI-FAIR"
}
```

2. All attribute names are expected to be present, but optional attributes (required=false) may take an empty string as
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

| Global Attributes            | Description                                                                                                                     | Compliance test          | Required | Multiple | 
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------|--------------------------|----------|----------|
| date_created                 | Creation date                                                                                                                   | data_type#str            | true     | false    |
| Conventions                  | conventions used in the dataset  (e.g. OceanSITES, ACDD, etc.)                                                                  | data_type#str            | false    | true     |
| institution_edmo_code        | EDMO code of the creator's organization                                                                                         | edmo_code                | true     | true     |
| institution_edmo_uri         | URI pointint to the EDMO page de of the creator's organization                                                                  | edmo_uri                 | true     | true     |
| geospatial_lat_min           | The southernmost latitude, a value between -90 and 90 degrees                                                                   | coordinate#latitude      | true     | false    |
| geospatial_lat_max           | The northernmost latitude, a value between -90 and 90 degrees                                                                   | coordinate#latitude      | true     | false    |
| geospatial_lon_min           | The westernmost longitude between -180 and 180                                                                                  | coordinate#longitude     | true     | false    |
| geospatial_lon_max           | The easternmost longitude between -180 and 180                                                                                  | coordinate#longitude     | true     | false    |
| geospatial_vertical_min      | Minimum depth of measurements in metres (negative for above sea level)                                                          | coordinate#depth         | true     | false    |
| geospatial_vertical_max      | Maximum depth of measurements in metres (negative for above sea level)                                                          | coordinate#depth         | true     | false    |
| time_coverage_start          | Start date of the data in UTC                                                                                                   | data_type#datetime       | true     | false    |
| time_coverage_end            | End date of the data in UTC                                                                                                     | data_type#datetime       | true     | false    |
| update_interval              | Update interval for the file (following ISO 8601). Use “void” for data <br/>that are not updated                                | data_type#str            | true     | false    |
| site_code                    | EMSO site code of the platform                                                                                                  | emso_site_code           | true     | true     |
| emso_facility                | EMSO facility name                                                                                                              | emso_facility            | false    | true     |
| source                       | Platform type name, should be a [L06](http://vocab.nerc.ac.uk/collection/L06) prefered label (prefLabel)                        | sdn_vocab_pref_label#L06 | false    | false    |
| platform_code                | OceanSITES platform code (leave blank if it does not exist)                                                                     | data_type#str            | false    | true     |
| wmo_platform_code            | [WMO](https://wmo.int) platfrom code (leave blank if it does not exist)                                                         | data_type#int            | false    | true     |
| data_type                    | Type of data, in most cases 'OceanSITES data time-series data'                                                                  | oceansites_data_type     | false    | false    |
| format_version               | OceanSITES format version                                                                                                       | equals#1.4               | false    | false    |
| network                      | List of the networks                                                                                                            | data_type#str            | true     | true     |
| data_mode                    | Data mode from OceanSITES table 4, possible values are "R" (real-time),<br/> "P" (provisional), "D" (delayed-mode), "M" (mixed) | oceansites_data_mode     | false    | false    |
| title                        | Free-format text describing the dataset, for use by human readers                                                               | data_type#str            | true     | false    |
| summary                      | Longer free-format text describing the dataset                                                                                  | data_type#str            | true     | false    |
| keywords                     | Please use one of ‘GCMD Science Keywords’, 'SeaDataNet Parameter Discovery <br/>Vocabulary' or 'AGU Index Terms' (ACDD)         | data_type#str            | false    | true     |
| keywords_vocabulary          | URI of the keywords vocabulary used                                                                                             | data_type#str            | false    | false    |
| project                      | Acronyms of the projects funding the dataset                                                                                    | data_type#str            | false    | true     |
| principal_investigator       | Name of the principal investigator                                                                                              | data_type#str            | true     | true     |
| principal_investigator_email | email of the principal investigator                                                                                             | email                    | true     | true     |
| doi                          | Digital Object Identifier (DOI) of the dataset                                                                                  | valid_doi                | false    | false    |
| license                      | Name of the license, use short identifier. Use of CC-BY-4.0 is strongly recommended                                             | spdx_license_name        | true     | false    |
| license_uri                  | URI pointing to a [SPDX](https://spdx.org/licenses/) license definition. Use of CC-BY-4.0 is strongly recommended               | spdx_license_uri         | true     | false    |

## Variable Attributes ##

The following table contains the attributes required to be compliant with EMSO Metadata Specification.

| Variable Attributes  | Description                                                                                                                                                     | Compliance test               | Required | Multiple |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|----------|----------|
| long_name            | human-readable label for the variable                                                                                                                           | data_type#str                 | true     | false    |
| standard_name        | Standard name within the Climate & Forecast standard, listed in [P07](http://vocab.nerc.ac.uk/collection/P07)                                                   | cf_standard_name              | true     | false    |
| units                | Variable units, should be the preferred label from a P06 definition                                                                                             | sdn_vocab_pref_label#P06      | true     | false    |
| comment              | free-text to add comments on the variable                                                                                                                       | data_type#str                 | false    | false    |
| coordinates          | Coordinates (or dimensions) of the variable, usually "TIME; DEPTH; LATITUDE;  LONGITUDE". Add "SENSOR_ID" <br/>if multiple sensors are used within this dataset | data_type#str                 | true     | true     |
| ancillary_variables  | Related variables, e.g. quality control flags, standard deviations, etc.                                                                                        | data_type#str                 | false    | true     |
| _FillValue           | Fill value                                                                                                                                                      | data_type#str                 | false    | true     |
| reference_scale      | reference scale of the variable (e.g. ITS-90 for temperature)                                                                                                   | data_type#str                 | false    | false    |
| sdn_parameter_name   | variable name (should be the preferred label from the P01 term)                                                                                                 | sdn_vocab_pref_label#P01      | true     | false    |
| sdn_parameter_urn    | variable code (should be an identifier from P01)                                                                                                                | sdn_vocab_urn#P01             | true     | false    |
| sdn_parameter_uri    | URI for the P01 term                                                                                                                                            | sdn_vocab_uri#P01             | false    | false    |
| sdn_uom_name         | Variable units, should be the preferred label from a P06 definition (duplicated to ensure compatibility with SeaDataNet)                                        | data_type#str                 | true     | false    |
| sdn_uom_urn          | Units identifier from SeaDataNet P06 vocabulary                                                                                                                 | sdn_vocab_urn#P06             | true     | false    |
| sdn_uom_uri          | Units URI from SeaDataNet P06 vocabulary                                                                                                                        | sdn_vocab_uri#P06             | false    | false    |
| sensor_model         | Sensor model (should be preferred label from the L22 term)                                                                                                      | data_type#str                 | true     | true     |
| sensor_manufacturer  | Sensor model (should be preferred label from the L35 term)                                                                                                      | data_type#str                 | true     | true     |
| sensor_reference     | sensor code (L22 identifier)                                                                                                                                    | data_type#str                 | true     | true     |
| sensor_serial_number | Unique identifier for the sensor                                                                                                                                | data_type#str                 | true     | true     |
| sensor_mount         | One of the possible sensor mounts from OceanSITES reference table 7                                                                                             | oceansites_sensor_mount       | true     | true     |
| sensor_orientation   | One of the possible sensor orientation from OceanSITES reference table 8                                                                                        | oceansites_sensor_orientation | true     | true     |

Although the 'ancillary_variables' term is not required, it is mandatory to set it in case there is a quality control
column related to the parameter.

## Quality Control Attributes ##

| QC Attributes | Description                                                                                                                   | Compliance test | Required |
|---------------|-------------------------------------------------------------------------------------------------------------------------------|-----------------|----------|
| long_name     | human-readable label, it is suggested to use parameter long_label and add "quality control flags" at the end                  | data_type#str   | true     |
| conventions   | OceanSITES QC Flags                                                                                                           | data_type#str   | true     |
| flag_values   | 0,1,2,3,4,5,6,7,8,9                                                                                                           | data_type#str   | true     |
| flag_meanings | unknown good_data probably_good_data potentially_correctable_bad_data bad_data nominal_value interpolated_value missing_value | data_type#str   | true     |

## Controlled Vocabularies ##

This metadata standard makes use of several controlled vocabularies from
the [NERC Vocabulary Service](https://vocab.nerc.ac.uk)

| vocab ID | description                               | URL                                                                       | 
|----------|-------------------------------------------|---------------------------------------------------------------------------|
| EDMO     | European Database of Marine Organizations | [EDMO](https://edmo.seadatanet.org/)                                      |
| ROR      | Research Organization Registry            | [ROR](https://ror.org)                                                    |
| P01      | parameter vocabulary                      | [P01](http://vocab.nerc.ac.uk/collection/P01)                             |
| P02      | parameter codes                           | [P02](http://vocab.nerc.ac.uk/collection/P02)                             |
| P06      | units                                     | [P06](http://vocab.nerc.ac.uk/collection/P06)                             |
| L05      | sensor types                              | [L05](http://vocab.nerc.ac.uk/collection/L05)                             |
| L06      | platform types                            | [L06](http://vocab.nerc.ac.uk/collection/L06)                             |
| L22      | sensor models                             | [L22](http://vocab.nerc.ac.uk/collection/L22)                             |
| SPDX     | software licenses                         | [github](https://github.com/spdx/license-list-data/blob/main/licenses.md) |

## Compliance Tests ##

* **data_type#type**: The parameter type is of a certain type. Possible arguments are 'float', 'str', 'int', 'date'
  and 'datetime'
* **edmo_code**: The parameter is an integer number representing an organization listed
  in [EDMO database](https://edmo.seadatanet.org/) (European Directory of Marine Organizations).
* **coordinate#type**: Checks if a coordinate is correct. The 'type' argument must be one of the following: '
  latitude', 'longitude' or 'depths'
* **emso_facility**: A valid name for an EMSO Regional Facility (EMSO_codes.md)
* **emso_site_code**: A valid name for an EMSO Site Code.
* **email**: valid email
* **oceansites_sensor_orientation**: A valid value from sensor_orientation table (OceanSites_codes.md)
* **oceansites_sensor_mount**: A valid value from sensor_orientation table (OceanSites_codes.md)
* **sdn_vocab_urn#vocab_id**: The parameter is a urn in a SeaDataNet vocabulary. Possible values are P01 (parameters),
  P02 (parameter codes), P06 (units), L05 (sensor types), L06 platform types) and L22 (sensor models)   P06 (units),
  L22 (devices), etc.
* **sdn_vocab_preflabel#vocab_id**: Preferred label from a SDN vocabulary
* **sdn_vocab_uri#vocab_id**: Resolvable URI for a SDN vocabulary Term
