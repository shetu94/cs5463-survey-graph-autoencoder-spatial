                                              CS 5463/4953 — Survey-Based Term Project
                                             Annotated Bibliography of Literature Found
                     Survey Title: Survey on Graph Convolutional Autoencoders for Spatial Shape Representation and Analysis


**Category I: Foundational Papers (4)**

[F1]  Kipf, T. N., & Welling, M. (2017). Semi-supervised classification with graph convolutional networks. ICLR 2017. URL: https://arxiv.org/abs/1609.02907
Annotation: This paper introduces the Graph Convolutional Network (GCN), a scalable framework for learning on graph-structured data using a layer-wise propagation rule derived from spectral graph convolutions. The model encodes both local graph structure and node features simultaneously, scaling linearly with the number of edges. It serves as the backbone architecture for most subsequent graph autoencoder models used in spatial shape encoding tasks.

[F2]  Kipf, T. N., & Welling, M. (2016). Variational graph auto-encoders. NIPS Workshop on Bayesian Deep Learning.
URL: https://arxiv.org/abs/1611.07308
Annotation: This work introduces the Variational Graph Auto-Encoder (VGAE), combining GCNs with the variational autoencoder framework for unsupervised learning on graphs. The encoder produces latent node embeddings using GCN layers, and a simple inner product decoder reconstructs graph structure. This is the direct precursor to spatial shape autoencoders, enabling compact and interpretable latent representations of graph-encoded shapes.

[F3]  Kingma, D. P., & Welling, M. (2014). Auto-encoding variational Bayes. ICLR 2014.
URL: https://arxiv.org/abs/1312.6114
Annotation: The foundational paper introducing the Variational Autoencoder (VAE), a generative model that learns continuous latent representations via the reparameterization trick. It establishes the probabilistic encoder-decoder framework that underpins VGAE and all subsequent graph-based autoencoders. The VAE's ability to produce smooth, semantically meaningful embeddings is critical for downstream similarity search in spatial datasets.

[F4]  Yan, X., Ai, T., Yang, M., & Tong, X. (2021). Graph convolutional autoencoder model for the shape coding and cognition of buildings in maps. IJGIS, 35(3), 490–512.
URL: https://doi.org/10.1080/13658816.2020.1768260
Annotation: This paper directly applies GCAE to the problem of building shape coding in cartographic maps. Building boundaries are modeled as graphs, and multiple vertex features capturing local and regional geometry are extracted. The unsupervised GCAE produces shape codes that outperform geometric baselines in similarity measurement, shape retrieval, and matching tasks — making it the most directly relevant foundational work for this survey.

**Category II: Recent Journal Papers (6)**

[J1]  Huang, Z., Khoshelham, K., & Tomko, M. (2022). A comparative study of various deep learning approaches to shape encoding of planar geospatial objects. ISPRS IJGI, 11(10), 527.
URL: https://www.mdpi.com/2220-9964/11/10/527
Annotation: This paper benchmarks multiple deep learning architectures — including CNNs, RNNs, and GCNs — for encoding planar geospatial object shapes such as building footprints and parcels. It evaluates encoding quality through shape retrieval tasks using cosine similarity in latent space. The comparative analysis provides a clear view of the trade-offs between different ML architectures, making it highly relevant for understanding when GCAEs outperform other approaches.

[J2]  Knura, M. (2024). Learning from vector data: Enhancing vector-based shape encoding and shape classification for map generalization. CaGIS, 51(1), 146–167.
URL: https://doi.org/10.1080/15230406.2023.2273397
Annotation: This study proposes enhanced preprocessing and feature engineering methods for vector polygon data fed into deep learning encoders for map generalization. It examines how input representation (vertex sampling, normalization, feature construction) affects classification and shape retrieval quality. The work highlights that architecture choice alone is insufficient — data representation significantly determines the performance of shape encoding models.

[J3]  Siampou, M. D., et al. (2024). Poly2Vec: Polymorphic encoding of geospatial objects for spatial reasoning with deep neural networks. arXiv:2408.14806.
URL: https://arxiv.org/abs/2408.14806
Annotation: Poly2Vec introduces a unified encoding scheme for heterogeneous geospatial objects — points, polylines, and polygons — into a common embedding space suitable for spatial reasoning tasks. The model uses transformer-based attention over coordinate sequences, enabling cross-type similarity comparisons. This approach addresses the limitation of architecture-specific encoders and shows strong performance in spatial retrieval and reasoning benchmarks.

[J4]  Michalopoulos, G., et al. (2024). Latent representation learning for geospatial entities. ACM Transactions on Spatial Algorithms and Systems.
URL: https://dl.acm.org/doi/10.1145/3663474
Annotation: This paper develops a latent representation learning framework for diverse geospatial entities by combining spatial context, geometry, and semantic attributes. The model generates dense embeddings suitable for downstream retrieval, clustering, and similarity tasks. It directly addresses the challenge of learning rich spatial embeddings that generalize across different geographic domains and entity types.

[J5]  Zhang, X., Touya, G., & Meijers, M. (2024). Automated map generalization: Emerging techniques and new trends. J. Geovisualization and Spatial Analysis, 8, 11.
URL: https://doi.org/10.1007/s41651-024-00174-4
Annotation: This editorial survey reviews recent deep learning techniques applied to automated cartographic generalization, covering tasks like building simplification, road network pruning, and symbol placement. It surveys CNN, RNN, and GNN-based methods and discusses challenges such as topological consistency and scale-dependent cognition. The paper provides a broad context for understanding where GCAE-based methods fit within the larger map generalization pipeline.

[J6]  Zhou, X., et al. (2024). Determining the optimal generalization operators for building footprints using an improved GNN model. Geocarto International, 39(1).
URL: https://doi.org/10.1080/10106049.2024.2306265
Annotation: This paper uses a graph neural network to classify and select the most appropriate generalization operators (simplification, aggregation, typification) for building footprints at multiple map scales. The GNN encodes building geometry and contextual relationships to predict operator selection, outperforming rule-based methods. It demonstrates how learned spatial shape representations can directly support cartographic decision-making tasks.

**Category III: Recent Conference Papers (10)**

[C1]  Park, J., Lee, D., Ham, J., & Baek, J. (2019). Symmetric graph convolutional autoencoder for unsupervised graph representation learning. ICCV 2019, pp. 6519–6528.
URL: https://arxiv.org/abs/1908.02441
Annotation: This paper introduces the Symmetric GCAE (S-VGAE), which uses a symmetric encoder-decoder structure to improve the quality of unsupervised graph embeddings. Unlike standard VGAE that uses only an inner product decoder, S-VGAE mirrors the encoder architecture in the decoder, producing more expressive latent representations. The approach is relevant for spatial shape encoding where both local vertex features and global graph topology need to be reconstructed faithfully.

[C2]  Litany, O., Bronstein, A., Bronstein, M., & Makadia, A. (2018). Deformable shape completion with graph convolutional autoencoders. CVPR 2018, pp. 1886–1895.
URL: https://arxiv.org/abs/1712.00268
Annotation: This paper applies graph convolutional autoencoders to 3D deformable shape completion, where partial or occluded 3D meshes are completed using learned shape priors. The GCAE encodes partial shapes into a latent space and decodes to full shape geometry. While focused on 3D shapes, its graph-based approach to encoding irregular geometric structures directly informs methods for 2D polygon shape completion in spatial datasets.

[C3]  Yu, Z., et al. (2024). PolygonGNN: Representation learning for polygonal geometries with heterogeneous visibility graphs. KDD 2024.
URL: https://dl.acm.org/doi/10.1145/3637528.3671884
Annotation: PolygonGNN constructs heterogeneous visibility graphs from polygon boundaries, connecting vertices based on geometric visibility relationships, and applies GNN message passing to learn shape embeddings. This richer graph construction captures both local curvature and global spatial structure better than simple boundary adjacency graphs. The model sets a new state-of-the-art on polygon shape similarity tasks and is among the most directly relevant recent papers for this survey.

[C4]  Ahn, S. J., et al. (2021). Variational graph normalized autoencoders. CIKM 2021, pp. 2827–2831.
URL: https://dl.acm.org/doi/10.1145/3459637.3482215
Annotation: This paper addresses a key weakness of VGAE poor embedding quality for isolated or low-degree nodes — by introducing L2-normalization in the latent space. The Variational Graph Normalized AutoEncoder (VGNAE) produces more uniformly distributed embeddings that better represent sparse nodes. For spatial shape graphs where boundary vertices can have uneven connectivity, this normalization is especially beneficial for producing consistent shape codes.

[C5]  Malkov, Y. A., & Yashunin, D. A. (2020). Efficient and robust approximate nearest neighbor search using HNSW. IEEE TPAMI, 42(4), 824–836.
URL: https://arxiv.org/abs/1603.09320
Annotation: This paper introduces Hierarchical Navigable Small World (HNSW) graphs for approximate nearest neighbor (ANN) search in high-dimensional embedding spaces. HNSW achieves logarithmic query complexity by organizing embeddings in a multi-layer proximity graph. It is the leading algorithm for similarity search over spatial shape embeddings, enabling real-time retrieval from millions of encoded shapes in GIS applications.

[C6]  Johnson, J., Douze, M., & Jégou, H. (2021). Billion-scale similarity search with GPUs (FAISS). IEEE Trans. Big Data, 7(3), 535–547.
URL: https://arxiv.org/abs/1702.08734
Annotation: FAISS (Facebook AI Similarity Search) is a GPU-accelerated library for efficient similarity search and clustering of dense vectors. It implements product quantization, inverted index structures, and GPU-parallelized exact and approximate search, scaling to billions of embeddings. For large-scale spatial datasets with millions of building footprints or polygons, FAISS provides the HPC infrastructure needed for practical shape retrieval systems.

[C7]  Feng, Y., Thiemann, F., & Sester, M. (2019). Learning cartographic building generalization with deep convolutional neural networks. ISPRS IJGI, 8(6), 258.
URL: https://doi.org/10.3390/ijgi8060258
Annotation: This paper applies CNNs to learn building simplification for cartographic generalization by treating building polygons as rasterized images. A U-Net-style encoder-decoder architecture learns to map complex building outlines to simplified versions at target map scales. It establishes CNNs as a viable alternative to graph-based approaches for shape simplification, though rasterization introduces resolution-dependent information loss compared to vector-native GCN methods.

[C8]  Fu, C., et al. (2024). Reasoning cartographic knowledge in deep learning-based map generalization with explainable AI. IJGIS, 38(10), 2061–2082.
URL: https://doi.org/10.1080/13658816.2024.2369535
Annotation: This paper integrates explainable AI (XAI) methods with GNN-based map generalization to interpret which shape features and spatial relationships drive automated generalization decisions. Using attention visualization and saliency maps, it reveals that GNNs capture cognitively meaningful shape properties. The explainability analysis validates the use of graph-based shape representations for cartographic tasks and helps identify which encoded features are semantically relevant.

[C9]  Mai, G., et al. (2023). On the opportunities and challenges of foundation models for geospatial artificial intelligence. arXiv:2304.04224.
URL: https://arxiv.org/abs/2304.04224
Annotation: This paper surveys the applicability of large foundation models (transformers pretrained on massive datasets) to geospatial AI tasks including shape encoding, spatial reasoning, and map understanding. It discusses how spatial inductive biases can be incorporated into transformer architectures and identifies key gaps between NLP/vision foundation models and geospatial requirements. The paper motivates exploring transformer-based alternatives to GCN encoders for spatial shape representation.

[C10]  Douze, M., et al. (2024). The FAISS library. arXiv:2401.08281.
URL: https://arxiv.org/abs/2401.08281
Annotation: This is the comprehensive reference paper for the FAISS library, detailing its full range of indexing algorithms including flat, IVF, PQ, HNSW, and their GPU variants. It describes the software engineering decisions behind billion-scale vector search and reports benchmark performance across multiple hardware configurations. As the primary HPC tool for similarity search over spatial shape embeddings, understanding FAISS indexing strategies is essential for implementing scalable spatial retrieval systems.

**Additional Papers: Other ML Architectures (Per Professor Feedback)**

[A1]  Zhang, H., et al. (2025). PSRT: A transformer-based approach for efficient geometric feature extraction from vector shape data. Applied Sciences, 15, 2383.
URL: https://www.mdpi.com/2076-3417/15/5/2383
Annotation: This paper applies transformer self-attention to vector polygon data, treating boundary vertices as token sequences to extract geometric shape features. The Polygon Shape Recognition Transformer (PSRT) captures long-range vertex dependencies that local GCN convolutions often miss. It demonstrates competitive performance on building shape classification tasks and represents an important non-GNN ML alternative for spatial shape encoding.

[A2]  Zhan, W., & Datta, A. (2024). Neural networks for geospatial data (NN-GLS). Journal of the American Statistical Association, 120(549), 535–547.
URL: https://arxiv.org/abs/2304.09157
Annotation: This paper integrates spatial autocorrelation structure into standard neural network architectures through a generalized least squares (GLS) loss, producing geospatially-aware embeddings that respect spatial dependency. The NN-GLS framework is applicable to any base architecture (MLP, CNN, GNN) and improves prediction accuracy on spatially correlated datasets. It highlights how spatial structure can be encoded beyond graph topology — relevant for HPC-scale geospatial applications.

[A3]  Mai, G., et al. (2023). On the opportunities and challenges of foundation models for geospatial AI. arXiv:2304.04224.
URL: https://arxiv.org/abs/2304.04224
Annotation: See annotation under [C9]. Listed here additionally under Other ML Architectures as it specifically addresses transformer and large language model architectures for geospatial shape understanding and spatial reasoning.

[A4]  Liu, Y., et al. (2025). Representation learning for geospatial data. Annals of GIS / International Journal of Digital Earth.
URL: https://www.tandfonline.com/doi/full/10.1080/19475683.2025.2552157
Annotation: This recent survey covers a spectrum of representation learning methods for geospatial data including graph-based, sequence-based (RNN/LSTM), and attention-based (transformer) approaches. It categorizes methods by data type (point clouds, polygons, raster grids) and identifies benchmark datasets for evaluation. The survey contextualizes where GCAEs sit relative to competing ML architectures for spatial data representation.


**Additional Papers: HPC Aspects (Per Professor Feedback)**

[H1]  Shao, Y., et al. (2024). Distributed graph neural network training: A survey. ACM Computing Surveys, 56(8), 1–39.
URL: https://dl.acm.org/doi/10.1145/3648358
Annotation: This comprehensive survey covers distributed training strategies for GNNs on large-scale graphs, including graph partitioning, mini-batch sampling, and communication-efficient gradient aggregation across multiple GPUs and nodes. It analyzes the computation vs. communication trade-offs specific to message-passing GNN architectures. For training GCAEs on city-scale building footprint datasets with millions of polygons, distributed training is essential — making this survey a key HPC reference.

[H2]  Dang, H., et al. (2024). GDL-GNN: Applying GPU dataloading of large datasets for graph neural network inference. Euro-Par 2024.
URL: https://link.springer.com/chapter/10.1007/978-3-031-69766-1_24
Annotation: This paper addresses the GPU memory bottleneck in GNN inference on large graphs by proposing an efficient GPU dataloading pipeline that streams graph batches directly to GPU memory. It achieves significant speedup on neighborhood sampling and feature aggregation compared to standard CPU-based dataloaders. The techniques are directly applicable to inference over large spatial graph datasets containing millions of building or polygon nodes.

[H3]  Armstrong, M. P., & Densham, P. J. (2020). High performance computing for geospatial applications: A prospective view. In High Performance Computing for Geospatial Applications. Springer.
URL: https://link.springer.com/chapter/10.1007/978-3-030-47998-5_15
Annotation: This chapter provides a broad view of HPC challenges specific to geospatial computing, including spatial indexing, parallel proximity queries, and distributed spatial data processing. It discusses how GPU acceleration and cluster computing enable real-time GIS operations at scale. The chapter provides foundational HPC context for understanding the computational requirements of large-scale spatial shape retrieval systems built on GCAE embeddings.
Note: This annotated bibliography covers 27 main papers to be read thoroughly, organized by category. Literature search is ongoing; updates will be reflected on the course GitHub repository: https://github.com/shetu94/cs5463-survey-graph-autoencoder-spatial
