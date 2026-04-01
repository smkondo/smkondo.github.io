---
title:  "Wind Comfort in Manhattan: Part 1 - Geometry Simplification V1.0"
mathjax: true
layout: post
image: /media/2026_0331_geometry_overview.png
description: "Automated geometry simplification of building massing using a Grasshopper Script in Rhino."
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/UzTBwVRbRT4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Table of Contents
1. [Background](#background)
2. [Introduction](#introduction)
3. [Methodology](#methodology)
4. [Limitations](#limitations)
5. [Future Improvements](#future-improvements)
   
## Background
As a wind engineer in New York City, I always get asked "where is the windiest parts of the city?" My response is always "near Hudson Yards" since it's near the river and surrounded by larger buildings that can catch oncoming high winds and bring them to pedestrian level. If you go to Hudson Yards during sunset on a windy day, you can experience first-hand the elevated gusts in the area compared to other parts of the city. As a seasoned wind engineer, this is my best estimate of the windiest location, but in all honesty, the solution is a lot more nuanced than just one location. There are multiple facets that can affect the windiest location including, but not limited to, width of the street, height of nearby buildings, oncoming wind direction/speed, and blockage from trees and other elements on the street. Since my professional life is understanding localized airflow effects using Computational Fluid Dynamics (CFD), I have decided to start a side project to quantify the winds in New York City using CFD. To limit the scope of this project, I have decided to first look at the borough of Manhattan before possibly expanding my analysis to the other four boroughs.

## Introduction
When setting up a CFD simulation, the first step is typically creating the computational domain that includes the geometry you wish to include in the simulation. In this investigation, the computational domain includes all the building massings in Manhattan that can fortunately be readily found online. While the building massing information is becoming more accessible, creating a CFD case is typically not as simple as plopping the 3D geometry into the solver and pressing go. There are three main things we need to ensure the CFD simulation runs smoothly.
1. All geometries inside the computational domain are water-tight to prevent any leakage from the domain
2. Sharp corners and small details must be removed to prevent meshing errors that can lead to numerical instabilities.
3. Geometries must be simplified to allow tractability of the simulation.

In this investigation where we are attempting to run a CFD simulation for a very large domain, the third point is especially important since it can be the difference of this simulation taking months instead of days to run.

The objective of this portion of the investigation is to take openly available building massing information from CAD Mapper and pre-processing them to be viable for a large-scale CFD simulation for urban microclimate. 

## Methodology
The custon Grasshopper script created for this portion of the investigation simplifies the building massing to ensure hex-dominant meshing is viable. The overall steps of the script are as follows:
1. Take the building and extract the floor layout of the building
2. Go through each point and remove any details that are less than 3ft in length.
3. Remove any sharp corners, curvilinear curves.
4. Create additional points that can help create a clean right angle.
5. Connect the curves and create a plane that is extruded to the height of the original building.

### Example 1: I-Shaped Building
Our first example is an I-shaped building located on 152nd Street between Amsterdam Ave. and Broadway (google maps view shown below).
![I_shape_satellite](/media/2026_0331_I_building_satellite.png)

The two videos below show the plan- and isometric-views of the simplification for this I-shaped building in Rhino using the Grasshopper script:
<iframe width="560" height="315" src="https://www.youtube.com/embed/P1jGzVqMsAE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/hL9JauIdkTk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Example 2: Building w/ Courtyard
Our second example is a Building with a Courtyard located on 145th Street between Broadway and Amsterdam Dr. (google maps view shown below).
![Courtyard_satellite](/media/2026_0331_courtyard_satellite.png)

The two videos below show the plan- and isometric-views of the simplification for this building w/ a courtyard in Rhino using the Grasshopper script:
<iframe width="560" height="315" src="https://www.youtube.com/embed/phJqogFt3vQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/1dTP6z-vgjo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Example 3: Entire City Block
Our third example is of an entire city block located between 147th and 148th Street between Amsterdam Ave. and Broadway (google maps view shown below).
![City_block_satellite](/media/2026_0331_city_block_satellite.png)

The two videos below show the plan- and isometric-views of the simplification for this city block in Rhino using the Grasshopper script:
<iframe width="560" height="315" src="https://www.youtube.com/embed/YshupbfrZ3o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/UzTBwVRbRT4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Current Limitations
There are a few limitations with the current cleaning script that was developed for this portion of the investigation. The main ones are:
1. The script can only simplify buildings that are a single height.
2. The script only takes into consideration the building itself. It does not consider the massing of the nearby buildings.

## Future Improvements
In the next iteration of this geometry simplification script, I would like to attempt to add the following features: 
1. Taking into consideration the adjacent buildings to see if they can be combined to create a single geometry.
2. Taking the simplified geometries from this script as training geometries to create a statistical model that can more appropriately simplify the input geometry.


The current script is not publicly available. If you are interested in using the scipt, please contact directly via email at shinyamkondo [at] gmail [dot] com. 

