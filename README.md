# Thesis repo for GNNs

Undergraduate thesis, Department of Computer Science and Engineering, Shahjalal University of Science and Technology (SUST).

This repository contains the implementation code for a heterogeneous GNN framework that uses a custom (proposed) loss function  for academic advisor-student matching via link prediction.

## Repository Structure

| File | Description |
|------|-------------|
| `CAMOC.ipynb` | CAMOC loss training and evaluation on the SUST academic knowledge graph |
| `CAMOC_dblp.ipynb` | CAMOC loss evaluation on the DBLP benchmark dataset |
| `camoc_gnn_pipeline_output.ipynb` | Full pipeline: CAMOC vs BCE comparison across GCN, GraphSAGE, GAT, RGCN, HAN |
| `loss_function_implementation.ipynb` | Standalone implementation of the CAMOC loss components |
| `Thesis_dataset_embed.ipynb` | Dataset construction and feature engineering for the SUST-AKG |
| `embedding.ipynb` | Node embedding generation and visualization |
| `gcn-link-prediction.ipynb` | Baseline GCN link prediction |
| `code_with_explanation.ipynb` | Annotated walkthrough of the core pipeline |

## Requirements

- Python 3.8+
- PyTorch
- PyTorch Geometric
- scikit-learn
- NumPy

All notebooks are designed to run on Google Colab with GPU runtime.

## Usage

1. Open any notebook in Google Colab
2. Set runtime to GPU
3. Run all cells

The SUST-AKG dataset files (`advisors.json`, `students.json`, `courses.json`, `research_areas.json`, `papers.json`) are loaded from the working directory. Upload them to `/content/` when running on Colab.

The DBLP notebook (`CAMOC_dblp.ipynb`) downloads the dataset automatically via PyTorch Geometric.

## GNN Architectures

The framework benchmarks five architectures under a unified evaluation protocol:

- GCN (Kipf and Welling, 2017)
- GraphSAGE (Hamilton et al., 2017)
- GAT (Velickovic et al., 2018)
- RGCN (Schlichtkrull et al., 2018)
- HAN (Wang et al., 2019)

## Author

Al Amin Hossain, CSE, SUST

## License

This project is part of an undergraduate thesis. No license is provided.
