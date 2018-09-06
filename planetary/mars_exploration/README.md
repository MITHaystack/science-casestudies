# Computer-aided exploration of the Martian geology

This set of notebooks aims at computing the favorability of selecting a site for landing on Mars. A favorable site depends on two main types of constraints:

- Landing constraints, which ensure that the system can land on a given area.
- Scientific targets, which must be visited by a rover after landing, if the rover can drive to them.

They were used to produce the results shown in [Computer-aided exploration of the Martian geology](https://doi.org/10.1029/2018EA000406), which was published in Earth and Space Science in 2018.

## Background

Motivated by growing amounts of data and enhanced resolution from orbiters and rovers, systems for computer‐aided decision support are becoming invaluable in planetary exploration. This article illustrates the value of such systems for a case study on the exploration of the Martian geology, along with improvements in assessing the favorability for landing. Under the current technical status quo for landing and rover's mobility, results show that Eastern Margaritifer Terra and Meridiani Planum stand out due to their high density of scientific targets and flat surfaces. However, our approach allows us to scale the analysis using different scenarios for the entire planet, quantifying the substantial benefits should higher landing elevations and higher rover speeds be realized in the future. This analysis offers new insights into the interplay of technical and scientific constraints.

## Content

### Code

The code implemented for this work is available in the open-source Python package [Scikit Discovery](https://github.com/MITHaystack/scikit-discovery) developed at MIT Haystack Observatory.

*&#9888; This code is mostly an unoptimized prototype, and running all the notebooks takes a long time.*

Scikit Discovery needs to be installed before running the notebooks, along with matplotlib, scikit-image, shapely, pandas, and scipy.

### Notebooks

We divided our work into seven notebooks, which perform an analysis for the entire planet at 20 pixels per degree (3 km per pixel at the equator) based on a rover similar to NASA's Mars 2020 rover. The notebooks must be run sequentially:

- The notebooks [1a](CaseStudyMars_20ppd_1a_LandingAndTraverseConstraints.ipynb) and [1b](CaseStudyMars_20ppd_1b_ScientificTargets.ipynb) detail where to get the input data (some of them are available in the folder [Original_Data](CaseStudyMars_Data/Original_Data), but most data must be downloaded manually), and convert them into a similar raster format.
- The notebooks [2a](CaseStudyMars_20ppd_2a_FuzzyCombination_LandingConstraints.ipynb) and [2b](CaseStudyMars_20ppd_2b_FuzzyCombination_ScientificTargets.ipynb) combine the rasters together into a single raw favorability map.
- The notebook [3](CaseStudyMars_20ppd_3_LandingEllipseUncertainty.ipynb) converts the raw favorability into a favorability by taking into account the uncertainty of the landing ellipse.
- The notebook [4](CaseStudyMars_20ppd_4_Analysis.ipynb) provides some ways of analyzing the results, for instance by looking at the distribution of the scientific targets that can be reached during a mission.
- The notebook [5](CaseStudyMars_20ppd_5_FutureCapabilities.ipynb) explores how the results vary when using enhanced rover capabilities.

### Favorability maps

We provide five maps produced by the notebooks in the folder [Results](CaseStudyMars_Data/Raster_Data_20ppd/Results):

- One map of [landing favorability](CaseStudyMars_Data/Raster_Data_20ppd/Results/Results_Favorability_Landing_25.tif), which takes into account the landing constraints only.
- Two maps of scientific favorability, one based on [neighboring relationships](CaseStudyMars_Data/Raster_Data_20ppd/Results/Results_Favorability_Scientific_Threshold_4_Scenarios_25_25.tif) between the scientific targets, and one based on [traverse paths](CaseStudyMars_Data/Raster_Data_20ppd/Results/Results_Favorability_Scientific_Paths_4_Scenarios_25_25.tif) to the scientific targets. Neighboring relationships require some high-priority targets to be located at less than a given driving time from the landing site. Traverse paths are more restrictive: all the high-priority targets must be reachable in less than the given driving time. Neighboring relationships are more suitable for a global analysis of potential landing sites, whereas traverse paths are more suitable for detailed analysis of the accessibility of a site.
- Two maps of selection favorability, one based on [neighboring relationships](CaseStudyMars_Data/Raster_Data_20ppd/Results/Results_Favorability_Selection_Threshold_4_Scenarios_25_25.tif) between the scientific targets, and one based on [traverse paths](CaseStudyMars_Data/Raster_Data_20ppd/Results/Results_Favorability_Selection_Paths_4_Scenarios_25_25.tif) to the scientific targets. These maps combine the landing and scientific favorability maps.

The following Python code is a minimal example showing how to open a map using GDAL and display it using matplotlib:
```
# Import packages
from osgeo import gdal
import matplotlib.pyplot as plt

# Define the folder where the raster maps are [modify if needed]
raster_folder = 'CaseStudyMars_Data/Raster_Data_20ppd/Results/'
# Choose the map to display [modify if needed]
raster_name = 'Results_Favorability_Selection_Threshold_4_Scenarios_25_25.tif'

# Open the map using GDAL, and read the values as a NumPy array
raster = gdal.Open(raster_folder + raster_name)
raster_array = raster.ReadAsArray()
# Compute the extent of the map
x_min, x_spacing, _, y_max, _, y_spacing  = raster.GetGeoTransform()
x_max = x_min + (raster.RasterXSize*x_spacing)
y_min = y_max + (raster.RasterYSize*y_spacing)

# Plot the map using Matplotlib
figure, subplot = plt.subplots()

image = subplot.imshow(raster_array,
                       extent = (x_min, x_max, y_min, y_max))
image_colorbar = plt.colorbar(image)
image_colorbar.set_label('Favorability')
                
plt.show()
```

## Contributing

We welcome any further use of or contribution to this project. Any question or comment can be addressed to Guillaume Rongier ([grongier@mit.edu](mailto:grongier@mit.edu)) or Victor Pankratius ([pankrat@mit.edu](mailto:pankrat@mit.edu)).

## Citation

If you use or further develop this work, please cite:

*Rongier G., Pankratius V. (2018) Computer-aided exploration of the Martian geology. Earth and Space Science, 5. DOI: 10.1029/2018EA000406*

```
@article{rongier_computer-aided_2018,
    title = {Computer-aided exploration of the Martian geology},
    volume = {5},
    doi = {10.1029/2018EA000406},
    journal = {Earth and Space Science},
    author = {Rongier, Guillaume and Pankratius, Victor},
    year = {2018}
}
```

## Acknowledgements

We acknowledge support from NSF ACI1442997 (PI: V. Pankratius) and NASA AISTNNX15AG84G (PI: V. Pankratius).