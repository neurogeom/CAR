# Data

Data available at <https://car.cvcd.xyz>.

## Usage

### Tools to Visualize All Data

You can use [CAR_WS_VR](https://github.com/neurogeom/CAR/releases/tag/v1.0.0) or [Vaa3D](https://github.com/Vaa3D/release) to visualize SWC format or APO format data.

### Data Type

#### Human

we listed 80 human neurons from 10 cortical neurons in surgical tissues of 10 patients  with brain tumors. The files are named using the following format: {neuron_id}_{patient_id}_{brain_region}.swc.

#### Mouse

Mouse Data includes complete neuron data, soma data and bouton data.

All data we provided has been registered to CCF-v3 (25um) space.

##### Complete Neuron / Axons

The data consists of 20 mouse neurons from 20 different cell types. The files are named using the following format: {brain_id}*{neuron_id}*{brain_region}.swc.

##### Somas

Soma morphometry is stored in a table with the following columns: Soma ID, fMOST BrainID, Soma_X(Raw brain, in voxel), Soma_Y(Raw brain, in voxel), Soma_Z(Raw brain, in voxel), Soma_X(CCFv3_25µm), Soma_Y(CCFv3_25µm), Soma_Z(CCFv3_25µm), Production platform, Registered CCF Region, Annotator.

##### Synaptic Sites (Boutons)

Boutons data are saved in the .apo format and is collected from 20 neurons. We offer two formats of bouton data:

1. `20_neuron_boutons_apo`:
   - These files are collected based on each soma brain region, and they are named using the following format: {brain_id}*{neuron_id}*{soma_brain_region}.apo.
2. `20_neuron_projection_boutons_apo`:
   - These files are collected based on each projection brain region, and they are named using the following format: r_{red}_g_{green}_b_{blue}_{brain_region}.apo.
