# Simulated Statistical Process with Mobile Network Data
Data and code repository for an end-to-end statistical process with simulated mobile network data

# Description
This is a repository for both data and code to execute an end-to-end statistical process from raw mobile telecommunication network event data to target population estimates. 

The structure of the statistical process is modular composed as a sequence of production steps. Data are synthetic generated by a [network event data simulator](https://github.com/MobilePhoneESSnetBigData/simulator) developed by Work Package I of the European project [ESSnet on Big Data II](https://webgate.ec.europa.eu/fpfis/mwikis/essnetbigdata/index.php/Main_Page).

# Data
Different types of data need to be integrated to reach final estimates about the target population. Basically:
* **Network configuration data**: data regarding how the mobile telecommunication network is configured. This data allows the analyst to build a so-called radio wave propagation model.
* **Network event data**: data regarding the digital trace of every device in the network (cell ID, Timing Advance, timestamp, etc.). 
* **Population data**: data from an external source to the network (certainly with coarser degree of space and time breakdown) with the kind of estimates about the whole target population.
* **Telecommunication market data**: data from the market of mobile telecommunications such as penetration rates or market shares.
* **Auxiliary information**: data from external sources providing information about land use, transport networks, and similar.

All data in this project are synthetic.

# Process
The whole process is designed according to a sequence of production process steps with some input data and input parameters and a throughput process producing output data and metrics (see figure).

 ![](/DataStepComplete.png)
 
 Apart from the generation of synthetic data from the network event data simulator, the modules are:
 
 * **Geolocation**.- This module focuses on providing location probability distributions for each mobile device accross the whole geographical territory of analysis.
 * **Deduplication**.- This module focuses on computing the probability that each device is carried out by a same individual together with more devices (device multiplicity).
 * **Statistical Filtering**.- This module focuses on identifying mobile devices corresponding to individuals of the target population (commuters, domestic tourists, etc.).
 * **Aggregation**.- This module focuses on providing probability distributions for the aggregate number of individuals detected by the network in different regions of the geographical territory of analysis.
 * **Inference**.- This module focuses on providing probability distributions for the aggregate number of individuals in the target population in different regions of the geoographical territory of analysis.
 
 # Folder Structure
 
 * **code**: it contains both the source code of standalone functions and packages and scripts to execute the statistical process.
 * **data**: it contains the sequence of input, intermediate, and output data of the whole process, organised in subfolders
   - *dupProb*: it contains the duplicity probability for each mobile device in the simulation.
   - *eventLocProb*: it contains the so-called event location probabilities associated to each grid tile and network event datum arising from the adopted radio wave propagation model.
   - *networkEvents*: it contains the data generated by each device in its interaction with the telecommunication network during its displacement.
   - *NnetDistrib*: it contains the probability distributions of the aggregated number of individuals detected by the network.
   - *NtargetDistrib*: it contains the probability distributions of the aggregated number of individuals in the target population.
   - *postLocProb*: it contains the probability distributions of each device location.
   - *simulatorConfig*: it contains the files with the configuration of the simulator providing the syntehtic scenario.
 * **metrics**: it contains graphical representations and images in general, (quality) indicators of the process, and log(s).
 * **param**: it contains both global parameters (in subfolder *resources*) and specific process parameters (in subfolder *process*). Information about the (simulated) ground truth is also contained here (in real production conditions this never exists).
 * *log*: it contains logs of the process execution.
 # MobileNetworkDataSimulationTemplate
