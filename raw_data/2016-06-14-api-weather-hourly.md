---
category: Raw data
path: '/raw_data'
title: 'weather/hourly'
type: 'GET'

layout: nil
---

Query hourly weather observations from NOAA\'s [Quality Controlled Local Climatological Data](http://cdo.ncdc.noaa.gov/qclcd/QCLCD?prior=N).


### Query Parameters


All query parameters are optional

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| wban_code               | The WBAN (Weather Bureau Army Navy) number is the unique identifier for weather stations                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| datetime                | In SQL datetime form (e.g. '2003-10-05 23:04:00')                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| old_station_type        | (Valid for all dates before May 1st, 2007) * AO1: automated station without a precipitation discriminator (no rain/snow sensor) * AO2; automated station with precipitation discriminator                                                                                                                                                                                                                                                                                                                                          |
| station_type            | * 0 AMOS now AWOS, also USAF stations * 4 MAPSO * 5 Navy METAR * 6 Navy Airways (obsolete) * 8 SOD; Keyed from 10C * 9 SOD; Keyed B-16, F6, Navy Forms * 11 ASOS (NWS) * 12 ASOS (FAA) * 15 Climate Reference Network                                                                                                                                                                                                                                                                                                              |
| sky_condition           | Up to three strings representing up to three layers of cloud cover. Each string is one of the below abbreviations with (in the case of clouds) a three-digit height following, representing hundreds of feet.  * CLR: Clear below 12,000 feet * FEW: > 0/8 - 2/8 sky cover * SCT (SCATTERED): 3/8 - 4/8 sky cover * BKN (BROKEN): 5/8 - 7/8 sky cover * OVC (OVERCAST): 8/8 sky cover                                                                                                                                              |
| sky_condition_top       | This parameter represents the highest observed sky condition (in hundreds of feet), taken from `sky_condition`.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| visibility              | Distance at which objects can be discerned, in statute miles                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| weather_types           | A multidimensional PostgreSQL array which contains values from [Federal Meterological Handbook No. 1: Surface Weather Observations and Reports](http://www.ofcm.gov/fmh-1/fmh1.htm), in the following six-tuple: [vicinity, intensity, desc, precip, obscuration, other]. For example, in the event of an observation of a thunderstorm with heavy rain and snow with fog, one might see: `[NULL, +, TS, RA, DG, NULL]`. But if it were also snowing, there would be an additional six-tuple: `[NULL, NULL, NULL, SN, NULL, NULL]` |
| drybulb_fahrenheit      | Current temperature at current level of humidity (in Fahrenheit)                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| wetbulb_fahrenheit      | The temperature the air **would** have at 100% humidity (in Fahrenheit)                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| dewpoint_fahrenheit     | The temperature at which water vapor condenses into water at the same rate at which it evaporates (in Fahrenheit)                                                                                                                                                                                                                                                                                                                                                                                                                  |
| relative_humidity       | Expressed as a percentage (0 to 100), the ratio of the partial pressure of water vapor to the saturated vapor pressure at the current temperature                                                                                                                                                                                                                                                                                                                                                                                  |
| wind_speed              | Observed wind speed (averaged?) (in miles per hour)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| wind_direction          | Observed wind direction (averaged?) in degrees (0 to 360)                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| wind_direction_cardinal | Observed wind direction (averaged?) as a human-readable direction, e.g. N, NE, NNE, NNW                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| station_pressure        | Average pressure in inches of Mercury                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| sealevel_pressure       | Average sea-level pressure in inches of Mercury                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| report_type             | Standard reports are denoted 'AA' and special reports (e.g. for tornadoes) are 'SP'. * AA: METAR (AVIATION ROUTINE WEATHER REPORT) - HOURLY * SP: METAR SPECIAL REPORT * CRN05: Climate Reference Network                                                                                                                                                                                                                                                                                                                          |
| hourly_precip           | Precipitation total (in inches)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |



### Query Operators


| Operator | Description                                                          |
|----------|----------------------------------------------------------------------|
| __gt     | greater than (`>`)                                                   |
| __ge     | greater than or equal to (`>=`)                                      |
| __lt     | less than (`<`)                                                      |
| __le     | less than or equal to (`<=`)                                         |
| __ne     | not equal (`!=`)                                                     |
| __like   | like value with % wildcards, case sensitive (`LIKE`, `'State%'`)     |
| __ilike  | like value with % wildcards, case insensitive (`ILIKE`,  `'state%'`) |
| __in     | within a list of provided values (`IN ('list', 'of', 'values')`)     |



### Response


Hourly weather observations and attributes (described above) that match the provided query parameters. Response is limited to 500 results, which can be paginated using the `offset` parameter.

