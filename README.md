# GeoSpatial_data_analysis
This project explores geospatial data analysis using  R with `sf`, `terra`, `ggplot2`, and `tmap`. 
It demonstrates vector and raster operations, spatial joins, and visualization with real-world datasets like London cycle hire stations and Luxembourg elevation data.

# Problem Statement
Geospatial data is essential for urban planning, environmental studies, transportation systems, and disaster management. However, raw geospatial data often contains inconsistencies, invalid geometries, or mismatched coordinate reference systems (CRS).
This project addresses these challenges by applying transformations, geometry fixes, and spatial operations to derive meaningful insights and visualizations.

# Features

1. Handling of vector data using the sf package
2. Handling of raster data using the terra package
3. Coordinate Reference System (CRS) transformations
4. Geometry operations: centroid, simplify, buffer, union, difference
5. Raster operations: crop, mask, classify, rasterize
6. Spatial joins and filtering
7. Visualization with ggplot2 and tmap
8. Integration of OpenStreetMap (OSM) and official datasets

# Errors Encountered and Fixes
1. Geometry Validity
Deprecated option: tmap_options(check.and.fix = TRUE)
Fix: Remove and use st_make_valid().

2. Invalid geometries breaking operations
Fix: Apply st_make_valid() after simplification.

Incorrect use of st_difference()
Fix: Use st_difference(a, b) with two layers, or use st_union() to merge.

3. Vector and Raster Interoperability
Using ext() and rasterize() on an sf object
Fix: Convert to a SpatVector with terra::vect().

4. Rasterize errors
Fix: Ensure CRS and geometry types match before rasterization.

5. Data Type Issues
Non-numeric attributes in mapping (capacity field)
Fix: Convert to numeric using as.numeric().

ifel function not found
Fix: Load terra package; use terra::ifel().

6. Code Structure
Split ggplot calls across chunks
Fix: Place all layers in one ggplot expression.

Duplicate pipelines
Fix: Maintain a single workflow (transform → simplify → validate → buffer/union).

