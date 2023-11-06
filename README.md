
![Overview of the CAR client software user interface. The CAR platform offers an array of diverse client software, each equipped with the ability to seamlessly interact with other clients, whether of the same type or different, through the CAR server. With the workstation (depicted by a blue icon), the virtual reality tool (yellow), or even the mobile app (orange), users can jointly explore neuronal data across multiple levels of resolution and execute various neuromorphometric tasks. Additionally, users may further access and curate neuronal data through the CAR game console (green).](./assets/banner.png)

# Collaborative Augmented Reconstruction for Scaled Production of 3D Neuron Morphology in Mouse and Human Brains

![species: mouse](https://img.shields.io/badge/species-mouse-blue.svg)
![species: human](https://img.shields.io/badge/species-human-green.svg)

Digital reconstruction of the intricate 3D morphology of individual neurons from microscopic images is widely recognized as a crucial challenge in both individual research laboratories and large-scale scientific projects focusing on cell types and brain anatomy. This task often fails both conventional manual reconstruction and state-of-the-art automatic reconstruction algorithms, even many of which are based on artificial intelligence (AI). It is also critical but challenging to organize multiple neuroanatomists to produce and cross-validate biologically relevant and agreeable reconstructions in scaled data production. Here we propose an approach based on collaborative human intelligence augmented by AI. Specifically, we have developed a Collaborative Augmented Reconstruction (CAR) platform for neuron reconstruction at scale. This platform allows for immersive interaction and efficient collaborative-editing of neuron anatomy using a variety of client devices, such as desktop workstations, virtual reality headsets, and mobile phones, enabling users to contribute anytime and anywhere and take advantage of several AI-based automation tools. We have tested CAR’s applicability for challenging mouse and human neurons towards a scaled and faithful data production. Our data indicate that the CAR platform is suitable for generating tens of thousands of neuronal reconstructions used in our companion studies.

## Structure of the repository

The repository consists of the CAR source code and the CAR generated data, including neuron reconstructions, detected boutons and 156,190 identified somas.

```
CAR
├── CAR-Game	# source code of CAR-Game client
├── CAR-Mobile	# source code of CAR-Mobile client
├── CAR-Server	# source code of CAR-Server
├── CAR-VR-WS	# source code of CAR-VR and workstation client
├── assets	# assets of documents
├── data	# paper supplementary data
│   ├── ...
│   └── README.md   # data-related supporting documents
├── docs	# sections of user manual
├── README.md
└── USER_MANUAL.md
```

## Instructions

The CAR platform includes a number of client tools and supports multiple data formats. A detailed [user manual](./USER_MANUAL.md) is provided.

The CAR project is released as open source and the executables are available at [Releases](https://github.com/neurogeom/CAR/releases).

Should there be any questions, please contact us or open an [issue](https://github.com/neurogeom/CAR/issues/new) on GitHub.

## Highlights of CAR
![image](https://github.com/neurogeom/CAR/assets/18539642/bcd0b434-fcb8-4dd1-8b87-df5051391679)
![image](https://github.com/neurogeom/CAR/assets/18539642/97e0e097-cdc1-43fb-b092-b2a56690d31b)
![image](https://github.com/neurogeom/CAR/assets/18539642/7795390d-0fcd-4ac0-9173-3770bb604b5e)
![image](https://github.com/neurogeom/CAR/assets/18539642/4e570c62-03e2-4974-9d9e-c89074bce7db)
![image](https://github.com/neurogeom/CAR/assets/18539642/a57d4113-140b-4016-9000-58b98e43ff50)


## Other resources

- [preprint](https://www.researchsquare.com/article/rs-3371435/v1)
- demo videos (more videos are being updated!)
  - Collaborative Augmented Reconstruction
 
    [![Collaborative Augmented Reconstruction](https://img.youtube.com/vi/_r1YsA9fas0/hqdefault.jpg)](https://youtu.be/_r1YsA9fas0)
  - Neuron reconstruction using CAR-VR
    
    [![Neuron reconstruction using CAR-VR](https://img.youtube.com/vi/kSK-HIsErpc/hqdefault.jpg)](https://youtu.be/kSK-HIsErpc)
  - Soma pinpointing using CAR-Mobile (Hi5)
 
    [![Soma pinpointing using CAR-Mobile](https://img.youtube.com/vi/8pA4QXjEviA/hqdefault.jpg)](https://youtu.be/8pA4QXjEviA)
  - Synapse validation using CAR-Mobile (Hi5)

    [![Synapse validation using CAR-Mobile](https://img.youtube.com/vi/DkwmJDUlai8/hqdefault.jpg)](https://youtu.be/DkwmJDUlai8)
  - AI-based agents in CAR
 
    [![AI-based agents in CAR](https://img.youtube.com/vi/xnw794lrpYU/hqdefault.jpg)](https://youtu.be/xnw794lrpYU)


