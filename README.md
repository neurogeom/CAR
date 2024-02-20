
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
### The Collaborative Augmented Reconstruction platform enables versatile morphometry in real-time

<img src="https://github.com/neurogeom/CAR/assets/81413763/fbff16f8-bd58-4b7e-86cd-afd40ebda20a" width="800">

CAR is designed to facilitate immersive collaboration among researchers and neuroscientists, enabling them to work together seamlessly on the reconstruction of neuronal morphology. The platform leverages the power of cloud computing and supports multiple client devices, including desktops, mobile devices, VR headsets, and gaming consoles, for efficient and interactive collaboration. Our primary focus with CAR is on studying the reconstruction of neuronal morphology in both mouse brains and human brains across different scales. To achieve this, CAR offers a wide range of task-specific functionalities. These include labeling 3D brain regions, reconstructing complete neurons in mouse brains, tracing local dendrites and axons in the human brain, identifying cell bodies, validating potential synaptic sites, and conducting various morphological reconstructions. Figure B provides a visual representation of the tasks and functionalities offered by CAR, showcasing its comprehensive approach to neuron data production and analysis. The CAR server exhibits its scalability and reliability in handling a substantial number of users and message-streams in real-time. Specifically, our measurements showed that the CAR server responded to incoming messages within a mere 0.27 milliseconds, even when dealing with a concurrency of 10,000 messages in Figure C. This indicates that the server’s performance remains robust and efficient, ensuring smooth interaction and communication between users and the platform. The ability to handle such a high volume of concurrent messages in real-time is a testament to the scalability and reliability of the CAR server architecture. It highlights the platform’s capability to support collaborative efforts among numerous users simultaneously, enabling efficient data annotation, validation, and reconstruction tasks.

### CAR reconstructs whole-brain projection neurons with converging correctness

<img src="https://github.com/neurogeom/CAR/assets/81413763/2a57148d-2e33-45dc-aeee-a917ee99aa4c" width="800">

It is evident that collaborative work among multiple individuals can indeed effectively enhance the accuracy of data annotation.  Figure A illustrates that the annotation results from different brain regions achieved an impressive accuracy rate of over 95%. This indicates that collaboration among multiple individuals significantly contributes to more accurate annotations. Figure B further highlights the importance of collaboration in data validation, particularly in obtaining accurate brain region projections. The projection mode demonstrates that introducing collaborative efforts among users greatly assists in achieving precise brain region projections. It is evident that without collaboration, there is a risk of incorrect projection patterns, as observed in the purple projection area. Throughout the different time stages of the annotation process, we observed that correct annotation structures gradually accumulate, resulting in higher accuracy levels. we defined a “normalized topological height” (NTH) for reconstruction nodes within a neuron . NTH indicates the corrective effort required to rectify a reconstruction error involving a particular node and all its subsequent branching structures. The magnitude of the height directly correlates with the cost of modification. There, we observed a gradual reduction in the proportion of incorrect reconstruction components over both the tracing stage and the NTH, reconstruction inaccuracies were promptly rectified before they could give rise to further erroneous structures as depicted in Figure C. Fortunately, users promptly identify and correct these errors in advance, thereby continuously improving the accuracy of the annotations. By maintaining good real-time accuracy through collaborative work, mutual agreement is fostered among users, leading to consistently higher levels of accuracy over time. This emphasizes the significance of ongoing collaboration and its positive impact on annotation accuracy.

### AI-based branch and terminal classifiers for automating reconstructions

<img src="https://github.com/neurogeom/CAR/assets/81413763/6fb890a4-2ada-4287-abcb-c6cac63194c2" width="800">

One of the key features in CAR is the integration of a Terminal Point Verifier (TPV) and a Branching Point Verifier (BPV), which play a crucial role in ensuring accurate results. With the assistance of TPV and BPV, CAR provides frequent reminders to human users, prompting them to correct any inaccurately reconstructed branching structures and resume tracing from forgotten breakpoints. Our observations throughout the entire reconstruction process have shown remarkable accuracy rates: TPV consistently achieves an average accuracy of over 90%, while BPV maintains an average accuracy of 85% (Fig. 3D, E). What sets CAR apart is its reliability in producing faithful hints for human curation, regardless of the completeness of the initial reconstructions. These AI tools work independently and provide reliable guidance to users, ensuring the integrity and accuracy of the final reconstructions. 

### Reconstruct human cortical dendrites in 10 brain regions

<img src="https://github.com/neurogeom/CAR/assets/18539642/4e570c62-03e2-4974-9d9e-c89074bce7db" width="800">

CAR stands out with its immersive visualization capability and the collaborative approach, allowing it to generate more stable and accurate results compared to alternative methods that lack optimized collaborative reconstructions. In a study comparing CAR and Vaa3D’s 3D-Viewer, two groups of annotators were assigned the same reconstruction task. The inter-group consistencies achieved using CAR and Vaa3D’s 3D-Viewer were 0.86 and 0.73 respectively, indicating a higher level of agreement among annotators when using CAR (Fig. 4C; Methods). The advantages of CAR become even more evident when working with human neuron images containing high levels of noise. For example, in a test using a randomly selected image (#00044), CAR achieved an 85% accuracy in reconstruction within 7.5 minutes, surpassing the performance of Vaa3D’s 3D-Viewer, which required 15 minutes but yielded inferior results with approximately 70% accuracy. A comparison with the 2-D visualization-based tool SNT showed that, despite requiring 20 minutes, SNT missed over 80% of neurites (Fig. 4D - left panel). Consistently, when comparing CAR with Vaa3D and SNT using 10 randomly selected neurons with expert-validated reconstructions, CAR demonstrated a convergence to over 80% accuracy within approximately 7.5 minutes. In contrast, Vaa3D and SNT achieved a maximum accuracy of 50% to 60% at the expense of nearly double or triple the reconstruction time. These findings highlight CAR’s superior performance in terms of accuracy, efficiency, and noise resilience, making it a valuable tool for reliable and efficient neuron reconstruction tasks.

### Reconstruct somas and synaptic sites at whole-brain scale

<img src="https://github.com/neurogeom/CAR/assets/81413763/6e8414de-d502-4016-884d-667e01f72a24" width="800">

Indeed, the collaborative nature of cloud platforms plays a crucial role in efficiently verifying large-scale tasks focused on specific brains. While automated algorithms can generate reasonable results, human validation remains essential to ensure the accuracy and meaningfulness of the obtained data.
In the case of soma detection in mouse brains, CAR leverages its collaborative framework to distribute the initial soma location resultsacross multiple mobile terminals. This enables rapid and on-the-go assistance in generating a large-scale dataset for cell body detection. The use of CAR’s mobile client allows remote users to fine-tune the soma locations in real-time, facilitating quick adjustments and refinements to improve the accuracy of the detections. By employing this protocol, we generated one of the most extensive databases of annotated somas, utilizing genetically labeled neurons across 58 whole mouse brains, which spanned a comprehensive total of 609 brain regions.
The utilization of the CAR platform also offers a remarkable advantage in simplifying the analysis of complex brain images, encompassing analyses at various scales, ranging from whole-brain analysis to the intricate connections between neurons at the synaptic level.
CAR's ability to perform precise axon tracing and reconstruction of spherical image objects, including somas proves particularly beneficial in alleviating the challenge of bouton validation. Boutons are small protrusions along neurite fibers that represent potential synaptic sites. With CAR’s accurate axon tracing and soma reconstruction, the identification and validation of boutons become more feasible. By leveraging the power of distributed computing and the collective efforts of remote users, CAR efficiently processes image-blocks containing putative somas and synapses.Remarkably, each image-block is typically annotated within a few seconds, highlighting the efficiency and effectiveness of the collaborative annotation process enabled by CAR.


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


