# BOON Guidelines for `network` and `site` Metadata

* This document describes the metadata fields `network` and `site` used in the [OG-1.0 format](https://github.com/OceanGlidersCommunity/OG-format-user-manual).
* The goal is to have BOON assets identified and easy to find within OceanOPS. Granularity is needed both in `network` attribution and `site` attribution. 
* These metadata fields will allow for better tracking of the BOON Task Team activity and assessement of the status of the task team toward its target.
* Values for the metadata fields can be flexible but will be managed in a vocabulary on GitHub to make it easier for data providers to best populate the fields and allow for cohesion.

---

## Network Metadata Field Background
A format for BOON `network` metadata values was chosen in 2022 (based on a meeting 9 December 2022 and follow-up correspondence). `network` values were selected for the 'California Underwater Glider Network (CUGN)' and 'Gliders in the Gulf Stream' programs and this documentation was drafted. These values have been tested and integrated into the near-real-time data streams for these programs through to the OceanGliders data system. With this format, the data provider chooses an NCEI Sea Name to provide an indicator of the region for their glider operations. Multiple network attributions are allowed. To implement this use a comma to separate each network entry.

**Example BOON `network` entries**
* OceanGliders > BOON > Northeast Pacific Ocean > California Underwater Glider Network
* OceanGliders > BOON > Northwest Atlantic Ocean > Gliders in the Gulf Stream



---


## How this looks in metadata
The metadata scheme below can be used with any NetCDF format currently used to store glider data. This includes the EGO, IOOS glider DAC and IMOS glider formats. The [OG-1.0 format](https://github.com/OceanGlidersCommunity/OG-format-user-manual) has also been designed to handle this information.

The two concepts described below, `network` and `site` should be included in the NetCDF global attributes with a string data type. 


## Definition
### Network
A **network** is a regroupment of platforms, crossing the boundaries of the program. It is usually virtual and represents a common effort or way to measure data. It can represent a mutualized scientific/geographical goal (array), or logistical/fundings/etc. approach.
Within BOON a network may refer to a regional array consisting of multiple sites (e.g., the California Underwater Glider Network) or an area of repeated glider operation (e.g., Gliders in the Gulf Stream)

The global attribute `network` follows this hierarchical format:
OceanGliders > BOON > [NCEI Sea Name](https://www.ncei.noaa.gov/data/oceans/ncei/vocabulary/seanames.xml) > *Your BOON Network Name*. (e.g., *OceanGliders > BOON > Northwest Atlantic Ocean > Gliders in the Gulf Stream*)
Where ">" is mandatory.

A list of `network` values is found here: [BOON network list](https://github.com/OceanGlidersCommunity/BOON/blob/main/VocabularyCollection/BOON%20networks.md#boon-networks-collection) and [BOON site list](https://github.com/OceanGlidersCommunity/BOON/blob/main/VocabularyCollection/BOON%20networks.md#boon-site-collection) and use it as the value in the **network** global attribute. If you would like to list more than one network you can use a comma to separate each network entry. This format requires that the network names themselves do not include commas. If your network is not in the list, request that it be added. See instructions in the 'request a new entry' section below. 



**Example BOON network metadata:**
| NetCDF global attribute | Data Type | Value |
|:-------|:-------|:-------|
| network | string | OceanGliders > BOON > Northwest Atlantic Ocean > Gliders in the Gulf Stream |

**Example with multiple networks:**
| NetCDF global attribute | Data Type | Value |
|:-------|:-------|:-------|
| network | string | OceanGliders > BOON > Northeast Pacific Ocean > California Underwater Glider Network, IOOS > SCCOOS, IOOS > CeNCOOS |


## Site
A **site** refers to the specific lines regularly monitored by gliders (e.g. *Balearic - Canales C1, CUGN Line 66*)

**Example site metadata:**
 NetCDF global attribute | Data Type | Value |
|:-------|:-------|:-------|
| network | string | CUGN Line 66|

**Example with multiple networks:**
| NetCDF global attribute | Data Type | Value |
|:-------|:-------|:-------|
| network | string | CUGN Line 66, CUGN Alongshore|

# Request a new entry
To request a new entry in the BOON Networks vocabulary and BOON Site vocabulary submit an issue in the [BOON repository](https://github.com/OceanGlidersCommunity/BOON) with the entry you would like to add to the vocabulary collection.

* In the case of **network**, you must provide the full value i.e. "OceanGliders > BOON > [NCEI Sea Name](https://www.ncei.noaa.gov/data/oceans/ncei/vocabulary/seanames.xml) > *Your BOON Network Name*."
* In the case of **site**, you must provide the name of the site, its waypoints and the parent [BOON Network](https://github.com/OceanGlidersCommunity/BOON/blob/main/VocabularyCollection/BOON%20networks.md).

