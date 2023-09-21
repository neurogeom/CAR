![The CAR platform allows various clients to access the cloud server, such as desktop workstations(blue), VR headsets(yellow), mobile phones(orange), and game console(green)](./assets/banner.png)

# Collaborative Augmented Reconstruction for Scaled Production of 3D Neuron Morphology in Mouse and Human Brains

![species: mouse](https://img.shields.io/badge/species-mouse-blue.svg)
![species: human](https://img.shields.io/badge/species-human-green.svg)

Digital reconstruction of the intricate 3D morphology of individual neurons from microscopic images is widely recognized as a significant challenge in both individual research laboratories and large-scale scientific projects focused on cell types and brain anatomy. This task often fails both conventional manual reconstruction and state-of-the-art automatic reconstruction algorithms, even many of which are based on artificial intelligence (AI). It is also crucial to organize multiple neuroanatomists to produce and cross-validate biologically relevant and agreeable reconstructions in scaled data production. We propose an approach based on collaborative human intelligence augmented by AI. Specifically, we have developed a Collaborative Augmented Reconstruction (CAR) platform for neuron reconstruction. This platform allows for immersive interaction and efficient collaborative-editing of neuron anatomy using a variety of client devices, such as desktop workstations, virtual reality headsets, and mobile phones, enabling users to contribute anytime and anywhere and take advantage of several AI-based automation tools. We have applied CAR to reconstructing challenging mouse and human neurons towards a scale and faithfulness that have never been demonstrated before.

## Directory Structure

The repository consists of CAR source code and supplementary material, including neuron reconstructions, detected boutons and 156,190 identified somas.

```
CAR
├── CAR-Game	# source code of CAR game client
├── CAR-Mobile	# source code of CAR mobile client
├── CAR-Server	# source code of CAR server
├── CAR-VR-WS	# source code of CAR VR and workstation client
├── assets	# assets of documents
├── data	# paper supplementary material
│   ├── ...
│   └── README.md   # data-related supporting documents
└── README.md
```

## Usage

CAR provides multiple clients, multiple interaction methods, and multiple data format support, so a detailed [user manual](./USER_MANUAL.md) is provided.

The source code of CAR developed is released as open source and the release is available at [Releases](https://github.com/neurogeom/CAR/releases).

## Questions

If you have any questions, please contact us or open an [issue](https://github.com/neu/issues/new) on GitHub.
