# Urban Computation Rhino Toolbar
This is a Rhino Toolbar with Urban Computation tools developed by the Design Technology team at Grimshaw.

## Installation
$\color{red}{\text{WIP}}$

## Commands
### BBOX
This command creates a rectangle with geographical information, that will serve as the boundary outline for all the other commands.

#### Inputs
- **EPSG**: The European Petroleum Survey Group code of the data you are bringing into the file, with 4326 as a default value.
- **Latitude**: The north-south position of the location you are looking for on Earth.
- **Longitude**: The east-west position of the location you are looking for on Earth.
- **Radius**: The Radious of area you want to search for, with center the point defined by Lan and Lon.
- **ESPG to re-project**: The ESPG code that you want to transform the data to. For the UK the default (27700) is the most commonly used.

####  Output
Curve: A rectangle that defines the selected boundary for urban data, baked inside layer *'UC::BBox'* with the following attributes.
  
| Key | Value|
| ---- |----- |
|BBox|maxX(double), minX(double), maxY(double), minY(double)|
|EPSG|code(int)|

### DEFRA
This command brings Habitat Data for the area inside the given BBOX. Terrain, Build Surfaces and Vegetation.

#### Input
BBOX

#### Ouput
Curves: Outlines of Habitat Data areas, in the layer *'UC::DEFRA'* with the following data as attributes.
  
| Key | Value|
| ---- |----- |
|OBJECTID| |
|ID| |
|A_pred||
|A_prob| |
|B_pred||
|B_prob| |
|SrcCode||
|ImagesSpr|Date - Date|
|ImagesAut||
|Shape__Area||
|Shape__Length||
|GlobalID||

### FLOODING
This command brings flooding information into Rhino.
#### Input
BBox
#### Ouput
Curves: Oulines of Risk Areas, Flood Zone 3 and Flood Zone 3 in layers *'UC::Flood::Risk_Areas'*, *'UC::Flood::Zone_2'* and *'UC::Flood::Zone_3'* respectively.

| Key | Value|
| ---- |----- |
|type||
|layer||
|type||
|shape_leng||
|gdb_geomattr_data||

### HERITAGE-ENGLAND
This command brings data about the England heritage
#### Input
BBox

#### Ouput
Curves: Outlines of the Listed Buildings, Scheduled Monuments,Parks and Gardens, Battlefields and World Heritage Sites with the following attributes

|  Key | Value|
| ---- |----- |
|OBJECTID||
|Northing||
|NGR||
|Name||
|ListEntry||
|ListDate||
|hyperlink||
|Grade||
|Easting||
|CaptureScale||
|area_ha||
|AmendDate||

### ISOCHRONES
#### Input

#### Ouputs

### LANDSAT
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



### OSM
This command brings Open Street Data about activities into Rhino.
#### Input
BBox
#### Ouputs
Points:  Activities locations, in layer *'UC::OSM'*, with the following attributes

### OS
This command brings data from the UK ordnance survey into Rhino
#### Input
BBox
#### Ouputs


## Tutorials
Video tutorials for UC toolbar use [here]()
$\color{red}{\text{WIP}}$
