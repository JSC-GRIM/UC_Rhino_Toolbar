# Urban Computation Rhino Toolbar
This is a custom Rhino toolbar developed by the Design Technology team at Grimshaw. It provides a suite of tools tailored for urban analysis, spatial computation, and data-driven design workflows within Rhino.

## Installation
### System requirements 
Rhino 8
### Installation 
**WIP**
1. Package Manager
2. Yak file

## Features
List of the tools

<details>
<summary><strong>BBOX</strong></summary>  
Generates a georeferenced rectangular boundary based on a specified location and search radius. This boundary acts as the spatial extent for all subsequent urban computation operations. The resulting rectangle is projected into the desired coordinate system and baked into the Rhino model. Metadata attributes are attached directly to the Rhino object and can be viewed in the Properties tab under the Attributes section.
  
#### Inputs
| Input | Description|
| ---- |----- |
|**EPSG**| The EPSG code of the input data's coordinate system. Default is 4326.|
|**Latitude**| The north-south position of the target location.|
|**Longitude**| The east-west position of the target location.|
|**Radius**| The radius (in meters) around the Lat/Lon point to define the boundary extent.|
|**ESPG to re-project**| The target EPSG code for reprojecting the boundary. Default for UK is 27700.|

####  Output
| Output | Description|
| ---- |----- |
|**Curve**| A rectangular boundary curve baked into the layer *UC::BBox*.|

#### Attributes
The output curve includes attributes that define its spatial extent and projection.
| Key | Value | Description|
| ---- |----- |----- |
|**BBox**|`array<double>`|An array containing the rectangle's maxX, minX, maxY, and minY coordinates.|
|**EPSG**|`int`|The EPSG code representing the coordinate system used for projection.|
</details>


<details>
<summary><strong>DEFRA</strong></summary>  
This command retrieves habitat data from DEFRA for the area defined by the input boundary (BBox). It includes terrain, built surfaces, and vegetation layers. The data is imported as curves representing habitat outlines and is baked into the Rhino model for spatial analysis.
  
#### Input
| Input | Description|
| ---- |----- |
|**BBox**|A georeferenced boundary rectangle defining the area of interest.|

#### Ouput
| Output | Description|
| ---- |----- |
|**Curves**| Outlines of Habitat Data areas, in the layer *'UC::DEFRA'* with the following data as attributes.|

#### Attributes
Each curve object includes the following attributes, visible in Rhino’s Properties tab:
| Key | Value | Description|
| ---- |----- |----- |
|**OBJECTID**|`int`|Unique identifier for the habitat feature.|
|**ID**|`string`|Feature ID.|
|**A_pred**|`float`|Prediction value A.|
|**A_prob**|`float`|Probability value A.|
|**B_pred**|`float`|Prediction value B.|
|**B_prob**|`float`|Probability value B.|
|**SrcCode**|`string`|Source code of the dataset.|
|**ImagesSpr**|`date`-`date`|Spring imagery date.|
|**ImagesAut**|`date`-`date`|Autumn imagery date.|
|**Shape__Area**|`float`|Area of the habitat shape.|
|**Shape__Length**|`float`|Perimeter length of the habitat shape.|
|**GlobalID**|`string`|Global unique identifier.|

</details>

<details>
<summary><strong>FLOODING</strong></summary>

### FLOODING
This command imports flood risk data into Rhino for the area defined by the input BBox. It includes outlines of flood zones and risk areas, categorized into distinct layers for clarity and further analysis.

#### Input
| Input | Description|
| ---- |----- |
|**BBox**|A georeferenced boundary rectangle defining the area of interest.|

#### Ouput
| Output | Description|
| ---- |----- |
|**Curves**|Flood zone outlines baked into the following layers: *UC::Flood::Risk_Areas*, *UC::Flood::Zone_2*, *UC::Flood::Zone_3*|

#### Attributes
Each curve object includes the following attributes:

| Key | Value|Description|
| ---- |----- |----- |
|**type**|`string`|Classification of the flood zone or risk area.|
|**layer**|`string`|Source layer of the data.|
|**shape_leng**|`float`|Perimeter length of the flood zone shape.|
|**gdb_geomattr_data**|`string`| Geometry metadata from the geodatabase.|

</details>

<details>
<summary><strong>HERITAGE-ENGLAND</strong></summary>
This command imports heritage data from Historic England for the area defined by the input BBox. It includes spatial outlines of listed buildings, scheduled monuments, parks and gardens, battlefields, and World Heritage Sites. The data is baked into Rhino as curves, each enriched with metadata attributes for further analysis or reference.
  
#### Input
| Input | Description|
| ---- |----- |
|**BBox**|A georeferenced boundary rectangle defining the area of interest.|

#### Ouput
| Output | Description|
| ---- |----- |
|**Curves**|Heritage feature outlines baked into Rhino. Each curve includes metadata attributes and is organized by feature type.|

#### Attributes
Each output curve object includes the following attributes, visible in Rhino’s Properties tab:

|  Key | Value | Description|
| ---- |----- |----- |
|**OBJECTID**|`int`| Unique identifier for the heritage feature.|
|**Northing**|`float`|Northing coordinate (projected).|
|**NGR**|`string`|National Grid Reference.|
|**Name**|`string`|Name of the heritage asset.|
|**ListEntry**|`string`|Official listing entry ID.|
|**ListDate**|`date`|Date the asset was listed.|
|**hyperlink**|`url`|Link to the official Historic England entry.|
|**Grade**|`string`|Listing grade (e.g., Grade I, II, II*).|
|**Easting**|`float`|Easting coordinate (projected).|
|**CaptureScale**|`float`|Scale at which the data was captured.|
|**area_ha**|`float`|Area of the feature in hectares.|
|**AmendDate**|`date`|Date of last amendment to the listing.|

</details>

<details>
<summary><strong>ISOCHRONES</strong></summary>
This command generates isochrone maps—areas reachable within a given time or distance—from a specified location using different travel modes. It uses external APIs to compute accessibility zones and visualizes them as curves in Rhino, categorized by travel type.
  
#### Input
| Input | Description|
| ---- |----- |
|**Latitude**|Latitude coordinate in the EPSG system provided.|
|**Longitude**|Longitude coordintae in the EPSG system provided.|
|**Travel_Mode**|Travel Mode: walking, cycling, or public_transport.|
|**Travel_Distance**| Radius of analysis area in meters.|
|**API_KEY**|API key for accessing the isochrone service.|

#### Ouput
| Output | Description|
| ---- |----- |
|**Curve**| Outline of the isochrone area, baked into one of the following layers based on travel mode: *UC::Isochrones::walking*,*UC::Isochrones::cycling* or *UC::Isochrones::public_transport*|

#### Attributes
**could be added*
|  Key | Value | Description|
| ---- |----- |----- |
|**time** |`float`|Estimated travel time (in minutes) to reach the boundary of the isochrone.|
</details>

<details>
<summary><strong>LANDSAT</strong></summary>

#### Input

#### Ouputs

|  Key | Value|
| ---- |----- |
|Coastal/Aerosol||
|Blue||
|Green||
|Red||
|Near Infrared (NIR)||
|SWIR 1||
|SWIR 2||
|Panchromatic||
|Cirrus||
|Thermal Infrared 1||
</details>

<details>
<summary><strong>OSM-ACTIVITIES</strong></summary>
This command brings Open Street Data about activities into Rhino.
  
| Input | Description|
| ---- |----- |
|**EPSG_in**| EPSG code from the Lat and Lon coordinates.|
|**Latitude**|Latitude coordinate in the EPSG system provided.|
|**Longitude**|Longitude coordintae in the EPSG system provided.|
|**EPSG_out**| EPSG code to reproject geometry to.|
|**Radius**| Radius of the analysis area (in meters).|

#### Ouput
| Output | Description|
| ---- |----- |
|**Points**| Activity locations baked into the layer *'UC::OSM_Activities'*. Each point includes metadata attributes.|

#### Attributes
|  Key | Value | Description|
| ---- |----- |----- |
|**value** |`string`|Specific activity or feature (e.g., bicycle_parking).|
|**sub_category** |`string`|Subtype or related category (e.g., bike).|
|**key** |`string`|OSM key (e.g., amenity, shop, leisure).|
|**category** |`string`|General classification (e.g., mobility, recreation, residential).|

</details>

<details>
<summary><strong>OS</strong></summary>
This command imports spatial data from the UK Ordnance Survey into Rhino, based on a selected layer and a defined geographic boundary. It provides detailed outlines of various geographic and infrastructural features, useful for urban analysis and contextual mapping.
  
| Input | Description|
| ---- |----- |
|**BBox**|A georeferenced boundary rectangle defining the area of interest.|
|**OS layer**| Selection of the Ordnance Survey data layer to import. Available options include: Airports, Boundaries, ETL, Foreshore, Greenspace, NationalParks, Rail, RoadsLocal, RoadsNational, RoadsRegional, Sites, Surfacewater, Waterlines, Woodland, LocalBuildings|

#### Ouputs
| Output | Description|
| ---- |----- |
| Curve | Geometric outlines of selected OS features, baked into Rhino. Each curve includes metadata attributes. |

#### Attributes
Each curve object includes the following attributes, visible in Rhino’s Properties tab:

|  Key | Value | Description|
| ---- |----- |----- |
|**UUID**|`string`|Unique identifier for the feature.|
|**SHAPE_Length**|`float`|Perimeter length of the shape.|
|**SHAPE_Area**|`float`|Area of the shape.|
|**OBJECTID**|`int`|Internal object ID.|
|**GmlID**|`string`|GML identifier from the source dataset.|

## Tutorials
Video tutorials for UC toolbar use [here]()
$\color{red}{\text{WIP}}$
