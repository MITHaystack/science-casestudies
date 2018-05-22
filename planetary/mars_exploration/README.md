# Computer-aided exploration of the Martian geology

This set of notebooks aims at computing the favorability of selecting a site for landing on Mars. A favorable site depends on two main constraints:

- Landing constraints which ensure that the system can land on a given area.
- Scientific targets which must be visited by a rover after landing, if the rover can drive to them.

We base our analysis on a rover similar to NASA's Mars 2020 rover at 20 pixels per degree (3 km per pixel at the equator), and investigate our ability to explore Mars with different scientific objectives and enhanced landing and roving capabilities.

We welcome any further use of or contribution to this project. Any question or comment can be addressed to Guillaume Rongier ([grongier@mit.edu](mailto:grongier@mit.edu)) or Victor Pankratius ([pankrat@mit.edu](mailto:pankrat@mit.edu)).

&#9888; The notebooks depend on the open-source Python package [Scikit Discovery](https://github.com/MITHaystack/scikit-discovery) developed at MIT Haystack Observatory. The code developed specifically for this work is more of an unoptimized prototype, and running all the notebooks takes a long time. Some of the input data are available in the folder *CaseStudyMars_Data*, the others must be downloaded as explained in the notebooks.

### Contributors

Guillaume Rongier, Victor Pankratius

### Acknowledgements

We acknowledge support from NSF ACI1442997 (PI: V. Pankratius) and NASA AISTNNX15AG84G (PI: V. Pankratius).
