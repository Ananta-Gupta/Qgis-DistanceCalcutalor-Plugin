# Qgis-DistanceCalcutalor-Plugin
# Working:
	This algorithm is use for calculating the distance between the river banks, distance till the flood line. 2nd algorithm is use for extracting surface water from the landsat-8 images.

(1st Algorithm)
# Steps to use the algorithm perfectly:
	1. Create and empty output folder in your working directory.
	2. Choose any one method to proceed with the algorithm.
	   (If choose method I, run 'ReferenceLineGenerator.py’ python script.)
			 		 or
	   (If choose method II, draw a refence line on the canvas, save the shp file with 'referenceLine.shp’ name.)
	3. Use QChanage plugin to generate equidistant point on the reference line.
	4. Save the QChanage file to output folder with 'chain_refLine.shp’ name.
	5. Run 'DistenceCalculator.py’ python script for calculating the distance.
	   (read the comments properly. Change the path as mentioned in the comments.)
	6. Algorithm finish.

# Method I – (by taking Bridge as a refence line)
	1. Generate start and end coordinates of the bridge and store then in a csv file.
  	2. Run 'ReferenceLineGenerator.py’ python script to generate a reference line perpendicular to the bridge.
  	3. Use QChanage plugin for generating equidistance points on the reference line.
  	4. Run 'DistenceCalculator.py’ python script to calculate the river bank length.

# Method II – (without Bridge reference)
  	1. Draw a reference line on the canvas parallel to the river water flow.
  	2. Use QChanage plugin for generating equidistant points on the reference line.
  	3. Run 'DistenceCalculator.py’ python script to calculate the river bank length. 

(2nd Algorithm)
# Steps for extracting Water from the Landsat-8 image:
# Method I – (using Python script)
	1. Run 'ReflectanceGenerator.py' python script.
  	2. Set the paths.
  	3. Run 'SurfaceWaterExtraction.py' python script to generate surface water.
  	4. (optional) Change the colours of the NDWI layer.

# Method I – (using Raster Calculator)
  	1. Open Raster Calculator.
  	2. Calculate Reflectance of the require band layer.
  	3. Calculate NDWI from the Reflectance layer.
  	4. Calculate surface water from NDWI layer.
  	5. (optional) Change the colours of the NDWI layer.
  		(all formulas are given below)

# Formulas:
	Reflectance: -
    	((0.0000200 * Landsat8_Band_no) + (-0.100)) / Cos(21.732483) * (3.141592 / 180)
  	NDWI: -
    	(Red - NIR) / (Red + NIR)
  	Surface Water: -
    	NDWI > 0
