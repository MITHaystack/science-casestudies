# DInSAR Simulator

These notebooks illustrate how to simulate synthetic interferograms for the study of surface deformations. The simulation relies on mimicking the scene that lead to those interferograms: a satellite passes over an area, sends a radar wave to the ground, and record the reflected signal. Each notebook details different features of the simulation process:

- [DInSAR_Simulator_Deformation_Models.ipynb](https://github.com/MITHaystack/science-casestudies/blob/master/geo/insar/simulator/DInSAR_Simulator_Deformation_Models.ipynb) presents several analytical models to simulate the source(s) of deformation.

- [DInSAR_Simulator_Topography.ipynb](https://github.com/MITHaystack/science-casestudies/blob/master/geo/insar/simulator/DInSAR_Simulator_Topography.ipynb) presents several ways to introduce the topographic component of an interferogram.

- [DInSAR_Simulator_Illapel_Earthquake.ipynb](https://github.com/MITHaystack/science-casestudies/blob/master/geo/insar/simulator/DInSAR_Simulator_Illapel_Earthquake.ipynb) presents a more complete case study, which mimic the interferogram of the 2015 Illapel earthquake, including atmospheric delays and temporal decorrelation.

We welcome any further use of or contribution to this project. Any question or comment can be addressed to Guillaume Rongier ([grongier@mit.edu](mailto:grongier@mit.edu)) or Victor Pankratius ([pankrat@mit.edu](mailto:pankrat@mit.edu)).

&#9888; The notebooks rely on the open-source Python packages [Scikit Data Access](https://github.com/MITHaystack/scikit-dataaccess) developed at MIT Haystack Observatory and [pyinsar](https://github.com/MITeaps/pyinsar) developed at MIT EAPS.

### Contributors

Guillaume Rongier, Cody Rude, Victor Pankratius, Thomas Herring

### Acknowledgements

We acknowledge support from NASA AISTNNX15AG84G (PI: V. Pankratius) and NSF ACI1442997 (PI: V. Pankratius).
