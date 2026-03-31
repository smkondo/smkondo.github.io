---
title:  "Wind Comfort in Manhattan: Part 1 - Geometry Simplification V1.0"
mathjax: true
layout: post
image: /media/2026_0331_geometry_overview.png
description: "Automatic geometry simplification of building massing using a Grasshopper Script in Rhino."
---
Background
As a wind engineer in New York City, I always get asked "where is the windiest parts of the city?" My response is always "near Hudson Yards" since it's near the river and surrounded by larger buildings that can catch oncoming high winds and bring them to pedestrian level. If you go to Hudson Yards during sunset on a windy day, you can experience first-hand the elevated gusts in the area compared to other parts of the city. As a seasoned wind engineer, this is my best estimate of the windiest location, but in all honesty, the solution is a lot more nuanced than just one location. There are multiple facets that can affect the windiest location including, but not limited to, width of the street, height of nearby buildings, oncoming wind direction/speed, and blockage from trees and other elements on the street. Since my professional life is understanding localized airflow effects using Computational Fluid Dynamics (CFD), I have decided to start a side project to quantify the winds in New York City using CFD. To limit the scope of this project, I have decided to first look at the borough of Manhattan before possibly expanding my analysis to the other four boroughs.

Introduction
* Geometry simplification is typically a bottleneck for large urban CFD simualtions. there is an increasing number of information provided for building parameters across the globe but using that information directly into CFD will most likely crash the simulation results. We need to simplify the 
* Creating the geometry domain is typically the first step of creating a CFD simulation. While CAD Mapper can provide a 3D model of the geometry, the geometry must be watertight and you also want to eliminate any extra details to reduce the computational cost of the simulation. Since we are attempting to understand the overall wind flow in Manhattan throughout the year, we do not need fine details on each of the buildings and a general overview of the building massing would be adequate for this analysis.
* The goal of this part of the project is to take the openly available building massing information and converting them to be suitable for a large CFD simulation for urban microclimate.

  
Methodology
* Using grasshopper to simplify the floor layout of the buildings. We want to remove any small details that are less than 3ft long. We want to remove any sharp corners and angles. If possible remove any curves that are curvilinear. 
* We are planning to use hex-dominant meshing.
* For I-shaped building
* For buiding with a courtyard
* For an entire city block
* The current script is not publicly available. If you are interested in using the scipt, please contact directly via email at shinyamkondo [at] gmail [dot] com. 

Current Limitations and Future Improvements
* Only considering buildings that are a single height
* Only considering a single building at a time. Does not consider the geometry of nearby buildings to influence the simplification.
* Future improvements will take into the consideration the impacts of adjacent buildings
* Future improvements will also attempt to use statistical learning to attempt to simplify buildings based on previous successful simplified buildings. The simplified geometries here can be used as training geometries to create a model that can predict the simplified geometries.
* 

[ventilator project](/media/Kondo_ColumbiaVentilatorChallenge.pdf)

![Ventilator](/media/ventilator.png)

