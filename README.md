# AIDAO-solution

The following is the instructions I've got on the olympiad.

Short review of fMRI
Functional Magnetic Resonance Imaging (fMRI) is a neuroimaging technique used to study brain activity by measuring changes in blood flow. Unlike standard MRI, which generates static images of brain anatomy, fMRI captures dynamic changes in neural activity over time. It does so by leveraging the Blood Oxygen Level-Dependent (BOLD) signal, which varies based on the oxygenation of hemoglobin. When neurons are active, they consume more oxygen, resulting in changes in the magnetic properties of hemoglobin. These changes can be detected and visualized by fMRI, allowing researchers to observe which areas of the brain are active in response to specific stimuli or tasks.

The data generated by fMRI consists of three-dimensional brain images, with each voxel representing a small region of brain tissue. Over time, these voxels produce time-series data that reflects changes in blood oxygen levels, forming what is essentially a four-dimensional dataset (space and time). Researchers can further process this data using parcellation schemes, which aggregate voxels into larger regions of interest (ROIs). The spatial resolution of these ROIs typically ranges from 30 to 500 components, depending on the study. Additionally, various denoising strategies are applied during time-series extraction to reduce noise and improve the signal quality.

These resulting time series are not independent; instead, they form complex patterns of brain functional organization. Importantly, this functional organization varies between individuals, a phenomenon that has been found to be both robust and reliable. Studies have shown that a person’s brain connectivity profile remains consistent across different scan sessions and even when performing different tasks or during rest. This means that an individual's connectivity fingerprint is intrinsic, allowing for identification based on brain connectivity patterns. More recent research has demonstrated that even short segments of fMRI data—less than a minute in length—can successfully identify individuals, further highlighting the uniqueness and stability of these connectivity patterns.

The ability to reliably identify individuals using fMRI functional connectivity has important implications for neuroscience and personalized medicine. By making inferences about brain function at the individual level, researchers could potentially develop more personalized diagnostic tools or interventions. For example, analyzing how a person's brain connectivity differs from typical patterns could inform treatment strategies for neurological disorders or cognitive decline. Furthermore, functional connectivity could be used to predict behavioral traits, mental health risks, or learning outcomes, making it a powerful tool for both research and clinical applications.

Task
Objective: Develop an algorithm capable of determining whether two given fMRI time-series samples belong to the same individual or not. This task can be viewed as an object matching problem, where the goal is to compare profiles of two brain scans and determine if they correspond to the same person.

Challenges:
The algorithm must account for variations in preprocessing methods, brain atlas parcellations, and eye states across samples.
Despite these variations, the algorithm must identify intrinsic patterns in the brain's functional connectivity that are stable across different conditions and reliably match individuals.
Data overview:
You are provided with unlabeled data for which labeling is to be computed. There are 20 subjects of fMRI scan in total, for each subject there are 16 (2x2x2x2) representations corresponding to – two different brain atlas partitions (Brainnetome and Schaefer200), times two different smoothing strategies, times two segments of scan sequence, times two different sequences. Shape structure for the dataset translates aas follows [20*16 objects, 10 timesteps from scan sequence, 246 number of features in larger atlas]. Note that since two atlases with different number of partitions are used, some data arrays are padded with np.nans, so that data shape is uniform.

Public Test Data:
IHB dataset: 10 subject

Private Test Data:
IHB dataset: 10 subjects

File with all 20×16 scan data representations is available in ihb.py.

Objective.
The task aims to simulate a realistic research workflow:

Data Collection Constraints: Collecting fMRI data is challenging and costly, resulting in small proprietary datasets.
Dataset Variability: These open datasets inherently differ from proprietary data in aspects such as scanner type, geographic location of data collection, and average age of participants. Such aspect are simulated through choice of different brain states, time sequences, atlas-based aggregations. The primary goal is to develop a model capable of identifying a person using fMRI as a "fingerprint" which is consistent across different perturbations and aspects of data.
Performance Metric and Deliverables
Evaluation Metric: Adjusted Rand Score (rescaled to be between 0.0 for random prediction and worse and 1.0 for perfect labeling.

Required Deliverables: - <name>.csv submission file that contains column named prediction which has same integer labels for objects corresponding to same class (subject's fMRI scan).

Output format
Upload your predictions into the system in the .csv format. The ﬁle has to contain at least a column named prediction and only this column would be considered by automatic checker.

References:

Lee, J., & Lee, J.-H. (2024). Discovering individual fingerprints in resting-state functional connectivity using deep neural networks. Human Brain Mapping, 45(1), e26561.
https://doi.org/10.1002/hbm.26561
