# Data

```
data
├── 20_mouse_neuron_boutons_data    # 20 boutons detected using CAR
│   └── 20_bouton_obj              # OBJ files for boutons, which contains information about the geometry of the 3D objects
│       ├── r_0_g_156_b_117_GU2_3.obj
│       ├── ...
│       └── r_97_g_231_b_183_COApm.obj
├── 20_mouse_neurons_data   # 20 mouse neuron morphology reconstructed using CAR
│   └── CCFv3_25um
│       ├── 17302_00002_stps.swc
│       ├── ...
│       └── 18869_5705_x4706_y6107_stps.swc
├── 80_human_neurons_data   # 80 human neuron morphology reconstructed using CAR
│   ├── 00011_P001_MFG.swc  # human neuron ID
│   ├── ...
│   └── 02322_P021_FL.swc
├── soma_morphometry_Hi5.xlsx	# 156,190 identified somas
└── README.md
```

## Usage

Neuron reconstructions are stored in SWC format, which is a simple and commonly used standardized format. 
Commonly used neuron morphology data analysis and visualization tools can directly read SWC format, such as [Vaa3D](https://github.com/Vaa3D/release). 
For detailed SWC format descriptions, please refer to [neuromorpho.org](https://neuromorpho.org/myfaq.jsp).

Bouton data are saved in OBJ format. The file format is open and has been adopted by other 3D graphics application vendors.

Soma morphometry is stored in a table with the following columns: Soma ID, fMOST BrainID, Soma_X(Raw brain, in voxel), Soma_Y(Raw brain, in voxel), Soma_Z(Raw brain, in voxel), Soma_X(CCFv3_25µm), Soma_Y(CCFv3_25µm), Soma_Z(CCFv3_25µm), Production platform, Registered CCF Region, Annotator.

All the original mouse brain images were downloaded from the [Brain Image Library (BIL)](http://www.brainimagelibrary.org). The original human brain images are available upon request due to their large sizes.

## Pre-process and Registration

All SWC data were preprocessed before analysis, where mouse brain data were also registered.

The following preprocessing steps were applied by using [Vaa3D](https://github.com/Vaa3D/release):

- connect to soma (define soma n=1 and parent=-1)
- sort nodes
- tip branch pruning: threshold=6 pixels
- resample: step=1

The mouse brain performs registration of the whole mouse brain to [CCFv3](https://atlas.brain-map.org/) using [mBrainAligner](https://github.com/reaneyli/mBrainAligner-web).
