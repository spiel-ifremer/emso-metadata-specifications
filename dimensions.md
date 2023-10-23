# Default Attributes for Dimensions #
This document contains the default dimension attributes expected in EMSO-compliant NetCDF files and ERDDAP services. 

## TIME ##

| Dimension Attributes | Description                                              |
|----------------------|----------------------------------------------------------|
| long_name            | time of measurements                                     |
| standard_name        | time                                                     |
| units                | days since 1950-01-01T00:00:00Z                          |
| sdn_parameter_name   | Elapsed time relative to 1950-01-01T00:00:00Z            |
| sdn_parameter_urn    | SDN:P01::ELTJLD01                                        |
| sdn_parameter_uri    | http://vocab.nerc.ac.uk/collection/P01/current/ELTJLD01/ |
| sdn_uom_name         | days                                                     |
| sdn_uom_urn          | SDN:P06::UTAA                                            |
| sdn_uom_uri          | http://vocab.nerc.ac.uk/collection/P06/current/UTAA/     |

## DEPTH ##

| Dimension Attributes | Description                                                            |
|----------------------|------------------------------------------------------------------------|
| long_name            | depth of measurements                                                  |
| standard_name        | depth                                                                  |
| units                | meters                                                                 |
| sdn_parameter_name   | Depth (spatial coordinate) relative to water surface in the water body |
| sdn_parameter_urn    | SDN:P01::ADEPZZ01                                                      |
| sdn_parameter_uri    | http://vocab.nerc.ac.uk/collection/P01/current/ADEPZZ01                |
| sdn_uom_name         | meters                                                                 |
| sdn_uom_urn          | SDN:P06::ULAA                                                          |
| sdn_uom_uri          | http://vocab.nerc.ac.uk/collection/P06/current/ULAA                    |

## LATITUDE ##

| Dimension Attributes | Description                                             |
|----------------------|---------------------------------------------------------|
| long_name            | latitude of measurements                                |
| standard_name        | latitude                                                |
| units                | degrees_north                                           |
| sdn_parameter_name   | Latitude north                                          | 
| sdn_parameter_urn    | SDN:P01::ALATZZ01                                       |
| sdn_parameter_uri    | http://vocab.nerc.ac.uk/collection/P01/current/ALATZZ01 |
| sdn_uom_name         | Degrees north                                           |
| sdn_uom_urn          | SDN:P06::DEGN                                           |
| sdn_uom_uri          | http://vocab.nerc.ac.uk/collection/P06/current/DEGN     |

## LONGITUDE ##

| Dimension Attributes | Description                                             |
|----------------------|---------------------------------------------------------|
| long_name            | longitude of measurements                               |
| standard_name        | longitude                                               |
| units                | degrees_east                                            |
| sdn_parameter_name   | Longitude east                                          | 
| sdn_parameter_urn    | SDN:P01::ALONZZ01                                       |
| sdn_parameter_uri    | http://vocab.nerc.ac.uk/collection/P01/current/ALONZZ01 |
| sdn_uom_name         | Degrees east                                            |
| sdn_uom_urn          | SDN:P06::DEGE                                           |
| sdn_uom_uri          | http://vocab.nerc.ac.uk/collection/P06/current/DEGE     |
