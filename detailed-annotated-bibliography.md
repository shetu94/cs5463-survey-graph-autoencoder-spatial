# CS 5463/4953 — Survey-Based Term Project
## Detailed Annotated Bibliography and Classification of Results

**Survey Title:** Graph Convolutional Autoencoders for Spatial Shape Representation and Analysis  
**Student:** Syeda Farjana Shetu | March 2026

---

## Overview

This document presents a detailed annotated bibliography of 27 papers selected for thorough reading as part of a survey on Graph Convolutional Autoencoders (GCAEs) for spatial shape representation and analysis. Papers are organized into six thematic classes that reflect the natural structure of the research area and will form the section-level organization of the final survey paper. Each entry includes a full citation, URL, role designation (Primary or Secondary), and a detailed annotation describing the problem addressed, methodology used, key contributions, and limitations.

---

## Classification Scheme

Papers are grouped into six natural thematic classes. **Primary** papers are most central to the survey topic and will be discussed in depth. **Secondary** papers provide supporting context and will be referenced more briefly.

### Class 1 — Graph-Based Spatial Shape Encoding *(Core Focus)*
| Tag | Paper | Role |
|-----|-------|------|
| [F2] | Kipf & Welling (2016) — Variational Graph Auto-Encoder | **Primary** |
| [F4] | Yan et al. (2021) — GCAE for Building Shape Coding & Cognition | **Primary** |
| [C1] | Park et al. (2019) — Symmetric Graph Convolutional Autoencoder | **Primary** |
| [C3] | Yu et al. (2024) — PolygonGNN: Heterogeneous Visibility Graph | **Primary** |
| [C4] | Ahn et al. (2021) — Variational Graph Normalized Autoencoder | Secondary |
| [C2] | Litany et al. (2018) — Deformable 3D Shape Completion with GCAE | Secondary |

### Class 2 — Foundational Neural Network Architectures
| Tag | Paper | Role |
|-----|-------|------|
| [F1] | Kipf & Welling (2017) — GCN for Semi-supervised Classification | **Primary** |
| [F3] | Kingma & Welling (2014) — Variational Autoencoder (VAE) | **Primary** |

### Class 3 — Alternative ML Architectures for Spatial Shape
| Tag | Paper | Role |
|-----|-------|------|
| [J1] | Huang et al. (2022) — Comparative Study: CNN vs. RNN vs. GCN | **Primary** |
| [J2] | Knura (2024) — Vector-Based Shape Encoding & Map Generalization | **Primary** |
| [J3] | Siampou et al. (2024) — Poly2Vec: Transformer-based Geospatial Encoding | Secondary |
| [A1] | Zhang et al. (2025) — PSRT: Transformer for Polygon Shape Features | Secondary |
| [A2] | Zhan & Datta (2024) — NN-GLS: Neural Networks for Geospatial Data | Secondary |
| [C7] | Feng et al. (2019) — CNN for Cartographic Building Generalization | Secondary |
| [C9] | Mai et al. (2023) — Foundation Models for Geospatial AI | Secondary |
| [A3] | Liu et al. (2025) — Representation Learning Survey for Geospatial Data | Secondary |

### Class 4 — Geospatial Entity Representation & Approximate Similarity Search
| Tag | Paper | Role |
|-----|-------|------|
| [J4] | Michalopoulos et al. (2024) — Latent Representation for Geospatial Entities | **Primary** |
| [C5] | Malkov & Yashunin (2020) — HNSW for Approximate Nearest Neighbor Search | **Primary** |
| [C6] | Johnson et al. (2021) — FAISS: Billion-Scale GPU Similarity Search | **Primary** |
| [C10] | Douze et al. (2024) — The FAISS Library | Secondary |

### Class 5 — Cartographic Generalization & Map Applications
| Tag | Paper | Role |
|-----|-------|------|
| [J5] | Zhang et al. (2024) — Automated Map Generalization: Emerging Techniques | **Primary** |
| [J6] | Zhou et al. (2024) — GNN for Building Footprint Generalization Operators | **Primary** |
| [C8] | Fu et al. (2024) — Explainable AI for Map Generalization | Secondary |

### Class 6 — HPC & Scalability for Spatial Deep Learning
| Tag | Paper | Role |
|-----|-------|------|
| [H1] | Shao et al. (2024) — Distributed GNN Training Survey | **Primary** |
| [H2] | Dang et al. (2024) — GPU Dataloading for Large-Scale GNN Inference | **Primary** |
| [H3] | Armstrong & Densham (2020) — HPC for Geospatial Applications | Secondary |

---

## Detailed Annotated Bibliography

---

### Class 1 — Graph-Based Spatial Shape Encoding

---

#### [F2] — PRIMARY
**Kipf, T. N., & Welling, M. (2016). Variational graph auto-encoders. NIPS Workshop on Bayesian Deep Learning.**  
🔗 [https://arxiv.org/abs/1611.07308](https://arxiv.org/abs/1611.07308)

> This paper combines a GCN-based encoder with the variational autoencoder framework to learn probabilistic latent representations of graph nodes without any supervision signal. The encoder maps each node to a Gaussian distribution in latent space using the graph structure and node features, and a simple inner product decoder reconstructs the adjacency matrix. Because no labeled training data is required, the model can be applied directly to spatial polygon graphs where shape category annotations are unavailable. The main architectural constraint is the inner product decoder, which reconstructs only edge probabilities and not vertex-level features — limiting the faithfulness of shape reconstruction. This is the foundational paper behind all GCAE-based spatial shape encoding methods in the survey.

---

#### [F4] — PRIMARY
**Yan, X., Ai, T., Yang, M., & Tong, X. (2021). Graph convolutional autoencoder model for the shape coding and cognition of buildings in maps. IJGIS, 35(3), 490–512.**  
🔗 [https://doi.org/10.1080/13658816.2020.1768260](https://doi.org/10.1080/13658816.2020.1768260)

> This is the most directly relevant paper to the survey's core topic. Building boundaries are modeled as cyclic graphs where each vertex holds features extracted at three spatial scales: local (adjacent vertex angles and edge lengths), regional (centroid-relative angle and distance), and global (total vertex count). A GCAE encodes these multi-scale features into compact shape codes through unsupervised training. Evaluation on building footprints from a Chinese city shows the codes support shape similarity ranking, retrieval, and matching with higher precision than classical descriptors such as Fourier and turning-function methods. The primary limitation is that experiments involve only one city and one building style, leaving the model's cross-city and cross-scale generalization untested.

---

#### [C1] — PRIMARY
**Park, J., Lee, D., Ham, J., & Baek, J. (2019). Symmetric graph convolutional autoencoder for unsupervised graph representation learning. ICCV 2019, pp. 6519–6528.**  
🔗 [https://arxiv.org/abs/1908.02441](https://arxiv.org/abs/1908.02441)

> The key contribution of this paper is identifying that VGAE's decoder — a simple inner product — discards node feature information and only reconstructs edge structure. The proposed Symmetric GCAE addresses this by using a GCN-based decoder that mirrors the encoder architecture, enabling simultaneous reconstruction of both adjacency structure and vertex features. This symmetric design produces better latent embeddings on node clustering and link prediction benchmarks. For spatial shape encoding, where polygon vertex features carry essential geometric information such as curvature, angles, and distances, the ability to reconstruct vertex features from the latent code makes this architecture preferable to standard VGAE for shape retrieval tasks.

---

#### [C3] — PRIMARY
**Yu, Z., Hu, Y., Li, Y., & Zhao, L. (2024). PolygonGNN: Representation learning for polygonal geometries with heterogeneous visibility graphs. KDD 2024, pp. 4012–4022.**  
🔗 [https://dl.acm.org/doi/10.1145/3637528.3671738](https://dl.acm.org/doi/10.1145/3637528.3671738)

> Prior polygon encoding methods treat each polygon independently and miss inter-polygon spatial relationships in multipolygon scenes. PolygonGNN constructs a heterogeneous visibility graph that connects boundary vertices both within each polygon and across different polygons through geometric visibility lines. A spanning tree sampling step controls graph density and reduces redundant edges while preserving key spatial relationships. The rotation-translation invariant vertex features ensure embeddings are robust to coordinate system variations. Experiments across five real-world and synthetic datasets show state-of-the-art performance on shape coding and building pattern classification. The visibility edge computation becomes a bottleneck for very large or highly concave polygons, which is noted as a limitation.

---

#### [C4] — Secondary
**Ahn, S. J., et al. (2021). Variational graph normalized autoencoders. CIKM 2021, pp. 2827–2831.**  
🔗 [https://dl.acm.org/doi/10.1145/3459637.3482215](https://dl.acm.org/doi/10.1145/3459637.3482215)

> Standard VGAE embeddings suffer from degree bias: high-degree nodes tend to dominate the latent space while low-degree nodes receive compressed, less informative representations. This paper resolves the issue by applying L2-normalization to all node embeddings, projecting them onto a unit hypersphere. The normalized embeddings are more uniformly distributed, which leads to improved performance on link prediction and clustering benchmarks. For spatial polygon graphs where boundary vertices at sharp corners may have very different connectivity compared to smooth boundary sections, this normalization promotes more consistent per-vertex shape code quality.

---

#### [C2] — Secondary
**Litany, O., Bronstein, A., Bronstein, M., & Makadia, A. (2018). Deformable shape completion with graph convolutional autoencoders. CVPR 2018, pp. 1886–1895.**  
🔗 [https://arxiv.org/abs/1712.00268](https://arxiv.org/abs/1712.00268)

> This paper demonstrates that GCAE latent spaces can encode sufficient structural information to generate complete shapes from partial or occluded 3D mesh inputs. A probabilistic GCN encoder maps partial geometry to a distribution over plausible completions, and a GCN decoder generates the full mesh. While the application domain is 3D surface meshes rather than 2D polygon boundaries, the core finding — that GCAE latent codes support generative reconstruction of missing geometric structure — has direct implications for 2D spatial use cases such as completing partially digitized building polygons or reconstructing missing boundary segments.

---

### Class 2 — Foundational Neural Network Architectures

---

#### [F1] — PRIMARY
**Kipf, T. N., & Welling, M. (2017). Semi-supervised classification with graph convolutional networks. ICLR 2017.**  
🔗 [https://arxiv.org/abs/1609.02907](https://arxiv.org/abs/1609.02907)

> This paper establishes the GCN propagation rule used in virtually all subsequent graph-based spatial methods. Each GCN layer aggregates features from direct graph neighbors using a symmetrically normalized adjacency matrix with added self-connections, then applies a learnable weight matrix and nonlinear activation. The model scales linearly with the number of edges, which is critical for large spatial graphs containing millions of polygon vertices. Stacking layers extends the receptive field across multi-hop neighborhoods. The well-known over-smoothing phenomenon — where adding more layers blurs out vertex-level distinctions — constrains practical GCAE encoder depth to typically two or three layers.

---

#### [F3] — PRIMARY
**Kingma, D. P., & Welling, M. (2014). Auto-encoding variational Bayes. ICLR 2014.**  
🔗 [https://arxiv.org/abs/1312.6114](https://arxiv.org/abs/1312.6114)

> The VAE formulates unsupervised representation learning as a variational inference problem: the encoder outputs parameters of a Gaussian distribution over latent codes, and the reparameterization trick makes the sampling step differentiable so gradients can flow through it during training. The resulting latent space has two desirable properties for shape analysis: continuity (small perturbations in latent space decode to similar shapes) and coverage (prior regularization encourages well-populated, non-degenerate latent regions). These properties make VAE-derived codes well-suited for downstream similarity search, where inter-code distances should reliably reflect geometric similarity between the corresponding polygon shapes.

---

### Class 3 — Alternative ML Architectures for Spatial Shape

---

#### [J1] — PRIMARY
**Huang, Z., Khoshelham, K., & Tomko, M. (2022). A comparative study of deep learning approaches to shape encoding of planar geospatial objects. ISPRS IJGI, 11(10), 527.**  
🔗 [https://www.mdpi.com/2220-9964/11/10/527](https://www.mdpi.com/2220-9964/11/10/527)

> This is the primary benchmark reference for understanding comparative performance of different ML architectures on geospatial shape encoding. CNN-based encoders operate on rasterized polygon images, which introduces resolution loss. RNN-based encoders treat the ordered vertex sequence as a time series, which is sensitive to starting vertex and traversal direction. GCN-based encoders represent the polygon as a graph and aggregate multi-hop neighbor features, producing the most geometrically faithful embeddings in shape retrieval experiments. The study evaluates all methods on the same building footprint datasets using cosine similarity-based retrieval, making comparisons fair. A gap is that only deterministic encoders are tested, leaving variational counterparts uncompared.

---

#### [J2] — PRIMARY
**Knura, M. (2024). Learning from vector data: Enhancing vector-based shape encoding for map generalization. CaGIS, 51(1), 146–167.**  
🔗 [https://doi.org/10.1080/15230406.2023.2273397](https://doi.org/10.1080/15230406.2023.2273397)

> This paper investigates how the preparation and representation of polygon vertex data before model training affects shape encoding quality. Key variables studied include vertex sampling strategy (uniform vs. curvature-adaptive), normalization of coordinate ranges, and construction of per-vertex features such as local curvature, edge length ratios, and interior angles. The study demonstrates that thoughtful preprocessing can match or exceed architecture-driven improvements, and proposes a standardized preprocessing pipeline for building polygon data. This is practically important because it provides a reproducible input preparation framework that can be combined with any downstream encoder including GCAEs.

---

#### [J3] — Secondary
**Siampou, M. D., et al. (2024). Poly2Vec: Polymorphic encoding of geospatial objects for spatial reasoning. arXiv:2408.14806.**  
🔗 [https://arxiv.org/abs/2408.14806](https://arxiv.org/abs/2408.14806)

> Poly2Vec addresses the challenge that real GIS datasets contain mixed geometry types — points, polylines, and polygons — that need to be jointly queried. A transformer-based architecture accepts any geometry as a sequence of coordinate pairs, using multi-head self-attention to capture dependencies between non-adjacent vertices. The model is trained with a contrastive objective to place geometrically similar objects closer in the shared embedding space. Cross-type similarity comparisons become possible, enabling mixed-geometry retrieval queries. The limitation is higher memory and compute cost compared to GCN encoders, particularly for polygons with many vertices.

---

#### [A1] — Secondary
**Zhang, H., et al. (2025). PSRT: A transformer-based approach for efficient geometric feature extraction from vector shape data. Applied Sciences, 15, 2383.**  
🔗 [https://www.mdpi.com/2076-3417/15/5/2383](https://www.mdpi.com/2076-3417/15/5/2383)

> PSRT applies transformer self-attention directly to polygon boundary vertices, treating each vertex as a token. The positional encoding is adapted for cyclic boundary sequences, avoiding artifacts from standard linear encodings applied to closed polygons. Multi-head attention allows each vertex to directly attend to any other boundary vertex, capturing long-range geometric dependencies that GCN message passing requires many layers to propagate. Experiments on building shape classification benchmarks show competitive accuracy compared to GCN methods, and the model avoids the graph construction step, simplifying the data pipeline.

---

#### [A2] — Secondary
**Zhan, W., & Datta, A. (2024). Neural networks for geospatial data (NN-GLS). JASA, 120(549), 535–547.**  
🔗 [https://arxiv.org/abs/2304.09157](https://arxiv.org/abs/2304.09157)

> NN-GLS identifies that standard neural network training ignores spatial autocorrelation — the tendency for nearby geographic observations to have similar characteristics. The method incorporates spatial dependence directly into the training loss using a generalized least squares formulation, which reweights training samples based on their spatial neighborhood structure. The approach is architecture-agnostic and can wrap around any base model including MLP, CNN, or GNN. For spatial shape datasets in urban areas where adjacent buildings often share architectural styles, incorporating spatial autocorrelation into training could improve embedding quality beyond what geometry-only inputs provide.

---

#### [C7] — Secondary
**Feng, Y., Thiemann, F., & Sester, M. (2019). Learning cartographic building generalization with deep convolutional neural networks. ISPRS IJGI, 8(6), 258.**  
🔗 [https://doi.org/10.3390/ijgi8060258](https://doi.org/10.3390/ijgi8060258)

> This is a baseline reference for CNN-based building generalization. Polygon boundaries are rasterized into binary images and fed into a U-Net encoder-decoder that learns to map complex building outlines to simplified versions at target map scales. The model trains on matched pairs of original and generalized polygons. Subsequent literature has noted that CNNs struggle to preserve right-angle constraints common in rectilinear buildings, and rasterization resolution limits the accuracy of reconstructed vector boundaries — a key limitation that motivates the shift to vector-native graph-based encoding approaches.

---

#### [C9] — Secondary
**Mai, G., et al. (2023). On the opportunities and challenges of foundation models for geospatial AI. arXiv:2304.04224.**  
🔗 [https://arxiv.org/abs/2304.04224](https://arxiv.org/abs/2304.04224)

> This paper surveys whether large pre-trained foundation models (transformers trained on massive corpora) can transfer to geospatial tasks. It identifies structural mismatches: geospatial data involves irregular geometries, multiple coordinate reference systems, and scale-dependent representations that standard tokenization does not handle naturally. Proposed adaptations include geography-aware positional encodings and multi-resolution input representations. The paper positions transformer-based polygon encoders within the broader trajectory of geospatial AI development and highlights open challenges in scaling foundation models to vector geometry data.

---

#### [A3] — Secondary
**Liu, Y., et al. (2025). Representation learning for geospatial data. International Journal of Digital Earth.**  
🔗 [https://www.tandfonline.com/doi/full/10.1080/19475683.2025.2552157](https://www.tandfonline.com/doi/full/10.1080/19475683.2025.2552157)

> This recent survey classifies representation learning methods for geospatial data across geometry type (point, polyline, polygon, raster), model family (graph-based, sequence-based, attention-based), and available evaluation benchmarks. It maps the current state of each approach and identifies data types where no dominant method yet exists. For this survey it provides a structured reference for situating GCAE-based polygon encoding within the full geospatial representation learning landscape and for identifying research gaps.

---

### Class 4 — Geospatial Entity Representation & Approximate Similarity Search

---

#### [J4] — PRIMARY
**Michalopoulos, G., et al. (2024). Latent representation learning for geospatial entities. ACM TSAS.**  
🔗 [https://dl.acm.org/doi/10.1145/3663474](https://dl.acm.org/doi/10.1145/3663474)

> This paper develops a multi-modal representation learning framework for geospatial objects that combines three information sources: geometric shape features, spatial context from neighboring entities, and semantic attributes from tags or land use categories. The combined embeddings support entity retrieval, spatial clustering, and similarity-based map matching with better performance than shape-only or attribute-only approaches. The key insight for this survey is that GCAE-produced shape embeddings can be significantly enriched by fusing spatial context, pointing toward a natural extension of pure shape encoding methods.

---

#### [C5] — PRIMARY
**Malkov, Y. A., & Yashunin, D. A. (2020). Efficient and robust ANN search using HNSW. IEEE TPAMI, 42(4), 824–836.**  
🔗 [https://arxiv.org/abs/1603.09320](https://arxiv.org/abs/1603.09320)

> HNSW builds a multi-layer proximity graph over embedding vectors where higher layers provide long-range navigation and the bottom layer supports local fine-grained search. Query time scales logarithmically with dataset size, making it practical for real-time retrieval from tens of millions of shape embeddings. The index is built incrementally and supports both exact and approximate queries depending on the search parameter. For a GCAE-based spatial shape retrieval system, HNSW provides the necessary approximate nearest neighbor infrastructure to make shape queries practical at GIS operational scale with acceptable recall-speed tradeoffs.

---

#### [C6] — PRIMARY
**Johnson, J., Douze, M., & Jégou, H. (2021). Billion-scale similarity search with GPUs (FAISS). IEEE Trans. Big Data, 7(3), 535–547.**  
🔗 [https://arxiv.org/abs/1702.08734](https://arxiv.org/abs/1702.08734)

> FAISS provides a comprehensive GPU-accelerated library for exact and approximate vector similarity search. It supports multiple indexing strategies including flat exhaustive search, inverted file indexing, product quantization for compressed vector storage, and HNSW. GPU acceleration enables billions of distance computations per second, making large-scale shape retrieval from national building footprint databases feasible in real time. The tradeoff between memory, speed, and search recall can be configured through quantization parameters, providing flexibility for different operational constraints.

---

#### [C10] — Secondary
**Douze, M., et al. (2024). The FAISS library. arXiv:2401.08281.**  
🔗 [https://arxiv.org/abs/2401.08281](https://arxiv.org/abs/2401.08281)

> This paper serves as the complete software documentation reference for FAISS, extending the original publication with newer index types, improved GPU memory management, and quantitative benchmarks across current hardware. It details how to select the appropriate combination of index type, quantization level, and GPU strategy based on dataset size, embedding dimension, and latency budget. For practitioners deploying a GCAE-based shape retrieval system, this is the primary implementation guide for configuring FAISS to balance retrieval quality against computational cost.

---

### Class 5 — Cartographic Generalization & Map Applications

---

#### [J5] — PRIMARY
**Zhang, X., Touya, G., & Meijers, M. (2024). Automated map generalization: Emerging techniques and new trends. J. Geovisualization and Spatial Analysis, 8, 11.**  
🔗 [https://doi.org/10.1007/s41651-024-00174-4](https://doi.org/10.1007/s41651-024-00174-4)

> This editorial survey maps the current landscape of deep learning approaches to automated cartographic generalization, covering building simplification, road network pruning, point cluster aggregation, and symbol placement. Methods are categorized by architecture — CNN, RNN, GNN, and transformer-based approaches — and evaluated on topological correctness, scale consistency, and generalization across map regions. Open challenges identified include multi-operator coordination and scale-consistent generalization. This paper is essential context for understanding real-world application requirements for GCAE-based spatial shape encoding systems.

---

#### [J6] — PRIMARY
**Zhou, X., et al. (2024). Determining the optimal generalization operators for building footprints using an improved GNN model. Geocarto International, 39(1).**  
🔗 [https://doi.org/10.1080/10106049.2024.2306265](https://doi.org/10.1080/10106049.2024.2306265)

> This paper applies a GNN to the operator selection problem in building generalization: given a building at a target map scale, the model predicts which operator — simplification, aggregation, typification, or elimination — should be applied. The GNN encodes building geometry and contextual relationships with neighboring buildings to predict the optimal operator, outperforming rule-based expert systems on a Chinese city building dataset. The work demonstrates that learned spatial shape representations can drive downstream cartographic decisions, bridging shape encoding research with operational GIS workflows.

---

#### [C8] — Secondary
**Fu, C., et al. (2024). Reasoning cartographic knowledge in DL-based map generalization with explainable AI. IJGIS, 38(10), 2061–2082.**  
🔗 [https://doi.org/10.1080/13658816.2024.2369535](https://doi.org/10.1080/13658816.2024.2369535)

> This paper applies gradient-based saliency maps and attention visualization to trained GNN-based map generalization models to understand which input shape features most influence the model's decisions. The analysis reveals that GNNs implicitly learn perceptually meaningful shape properties — such as compactness, elongation, and spatial density of neighboring buildings — without explicit feature engineering. This explainability work validates the cognitive relevance of learned graph-based shape representations and helps identify which geometric aspects of GCAE encodings are most informative for cartographic downstream tasks.

---

### Class 6 — HPC & Scalability for Spatial Deep Learning

---

#### [H1] — PRIMARY
**Shao, Y., et al. (2024). Distributed graph neural network training: A survey. ACM Computing Surveys, 56(8), 1–39.**  
🔗 [https://dl.acm.org/doi/10.1145/3648358](https://dl.acm.org/doi/10.1145/3648358)

> Training GNNs on large graphs requires distributing both graph structure and computation across multiple GPUs or compute nodes, introducing communication overhead when boundary nodes need to aggregate features from different machines. This comprehensive survey covers graph partitioning strategies that minimize cross-partition edges, mini-batch neighbor sampling methods that limit neighborhood expansion during training, and gradient synchronization approaches from fully synchronous to asynchronous SGD. For GCAE training on city-scale building polygon datasets with millions of vertices and edges, this survey provides essential guidance for scaling beyond single-GPU memory limits.

---

#### [H2] — PRIMARY
**Dang, H., et al. (2024). GDL-GNN: Applying GPU dataloading of large datasets for GNN inference. Euro-Par 2024.**  
🔗 [https://link.springer.com/chapter/10.1007/978-3-031-69766-1_24](https://link.springer.com/chapter/10.1007/978-3-031-69766-1_24)

> A key bottleneck in large-scale GNN inference is the data pipeline: constructing graph batches, sampling neighborhoods, and loading features from CPU to GPU memory can leave the GPU idle for significant portions of inference time. GDL-GNN addresses this by overlapping GPU computation with asynchronous CPU-side batch preparation and memory transfer using a multi-threaded prefetching pipeline, achieving near-full GPU utilization on large graph datasets. For encoding millions of building polygon graphs through a trained GCAE at inference time, this optimized dataloading is necessary to meet operational throughput requirements.

---

#### [H3] — Secondary
**Armstrong, M. P., & Densham, P. J. (2020). High performance computing for geospatial applications. In HPC for Geospatial Applications, Springer.**  
🔗 [https://link.springer.com/chapter/10.1007/978-3-030-47998-5_15](https://link.springer.com/chapter/10.1007/978-3-030-47998-5_15)

> This chapter provides foundational HPC context for geospatial workloads, reviewing parallel approaches to spatial indexing, proximity query processing, and distributed spatial join operations. It covers both MPI-based cluster computing and GPU-accelerated spatial processing. For understanding the full computational pipeline of a GCAE-based spatial shape retrieval system — from data ingestion through graph construction, encoder inference, embedding indexing, and query serving — this chapter provides the systems-level framing within which the deep learning components must be integrated.

---

*Note: Literature search is ongoing. Updates are reflected at: [https://github.com/shetu94/cs5463-survey-graph-autoencoder-spatial](https://github.com/shetu94/cs5463-survey-graph-autoencoder-spatial)*
