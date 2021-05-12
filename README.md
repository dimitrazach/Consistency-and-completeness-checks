# Consistency-and-completeness-checks
  ## An ArcMap Tool for checking topo-semantic consistency and completeness of a VGI dataset.
This Toolbox was developed to evaluate the quality of a VGI (Volunteered Geographic Information) dataset, such as OpenStreetMap. The purpose of this Toolbox is to implement automated checks for the quality of the dataset and in particular for its completeness and topo-semantic consistency. The GIS user enters his data (which are divided into thematic layers e.g. points of interests, buildings, roads, etc.), the area of interest and fills in the required fields in the tool he chooses to run each time. The tool is executed and presents the results qualitatively and quantitatively. In this way the user is able to be informed about the consistency, the topology and the completeness of his dataset, the errors that exist in his data and decide on their suitability for use.

![ArcMap Tool](https://user-images.githubusercontent.com/84000953/117939151-780e8c00-b310-11eb-93e9-08384c1ff486.png)

## Features
* Completeness checks based on the attribute field "type" of each thematic layer
* General topology checks (internal) for Linear (roads, railways, waterways) and Polygon (buildings, land use, nature) features
* Topo-semantic checks between POIs (points of interests) and the other thematic layers. In this case,  a number of rules check specific POIs (based on "type") that semantically related to certain layers, with these layers. For example, a cafeteria should be located inside a building and at the same time off the road, a tram stop should be located on a railway line and at the same time outside the building, etc.
* Prepare data (optional). A set of tools for data preparation that runs before the topo-semantic checks are applied

## Completeness checks
The  application of completeness checks of the tool can inform the user about both the lack or existence information on the values of the field referring to the type of thematic layers, as well as the variety of the types per layer.

## General topology checks (internal)
Internal logical consistency is associated with the topological relationships of spatial entities in a thematic layer. All polygonal entities (e.g. buildings, land use, nature polygons) can be checked for overlap and the existence of sliver polygons between them, the existence of gaps etc. All linear entities. (e.g. road network, rail network, hydrological network) can be checked for overlap, self-overlap, intersection, self – intersection etc.

## Topo – semantic consistency checks
A number of topo – semantic consistency checks are based on semantic information about POIs resulting from the “type” tag in relation to layers that are semantically related to them taking into account the position. POIs are checked to specific thematic layers (e.g. buildings, polygons of nature, road network, railway network).  In order to test the topo - semantic consistency, a set of rules is expressed through the following 6 categories.

* Points of Interest that must be inside Buildings (POIs must be inside buildings)
* Points of Interest that are semantically related to the Road Network and must be outside the Road Network (POIs of roads that must be outside of Roads)
* Points of Interest that are semantically related to the Road Network and must be located outside Buildings (POIs of roads that must be outside of Buildings)
* Points of Interest semantically related to the Road Network that should be on the Road Network (POIs that should be on Roads)
* Points of Interest that must be outside the polygons of Nature (POIs must be outside of Natural)
* Points of Interest that are semantically related to the Rail Network and should be located on the Rail Network (POIs that should be on Railways)

The tool applies the above topo–semantic constraints by implementing a set of check categories. In each of the cases, the incorrect spatial entities, are identified in the data set, labeled and reregistered as separate entities in the database. 

