# Neuron-Guided Genre Refinement in LLM-Based Recommender
Systems using QRNCA

## Overview
This project integrates **Query-Relevant Neuron Cluster Attribution (QRNCA)** with the **DLCRec** (Diversity-aware LLM-based Recommender) model to enhance genre prediction diversity in movie recommendations.

The approach identifies neuron clusters relevant to each movie genre and refines the genre prediction process by matching history genres with diverse genres having maximum neuron overlap.

## Project Structure
```
├── dlcrec/                   # DLCRec base model files
├── qrnca/                    # QRNCA neuron attribution scripts
├── data/                     # MovieLens dataset (genres, user history)
├── results/                  # Evaluation results and generated charts
  ├── contrib_Action.png
  ├── contrib_Comedy.png   
  ├── contrib_Romance.png
  ├── Base_Ablate_Amplify.png
  ├── genre_overlap_heatmap.png
  ├── output.png
  └── pipeline.png
                 # Final project report (IEEE style)
```

## Methodology Summary
1. **Base Model (DLCRec):**
   - Generates genre predictions from user history.
   - Uses LLaMA-3.1 (8B Instruct) as backbone.

2. **QRNCA Integration:**
   - Extracts neuron clusters responsible for each genre.
   - Builds a mapping between history and diverse genres via neuron overlap.

3. **Genre Refinement:**
   - Replaces diverse genres predicted by DLCRec with those sharing higher neuron similarity with history genres.

4. **Evaluation Metrics:**
   - Match, Precision, Recall, Jaccard Index.
   - Ablation studies for contribution weighting and neuron overlap.

5. **Visualizations:**
   - Per-neuron contribution graphs.
   - Inter-genre neuron overlap heatmap.
   - Ablation and accuracy comparison charts.

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/Susheel-Verma/Neuron-Guided-Genre-Refinement-in-LLM-Based-Recommender-Systems-using-QRNCA.git
   cd QRNCA-DLCRec
   ```

2. Install dependencies:
   ```bash
   make a environment with llama factory,it have all required dependencies.
   ```

3. Run genre refinement and evaluation:
   ```bash
   python untitled2.py
   ```

4. View results in the `/results` folder.

## Results Summary
| Configuration | Match | Precision | Recall | Jaccard |
|----------------|--------|------------|---------|----------|
| Full Model (QRNCA + Overlap + Contrib) | 0.27 | 0.87 | 0.20 | 0.20 |
| – No QRNCA Refinement | 0.003 | 0.58 | 0.91 | 0.55 |
| – No Neuron Overlap | 0.49 | 0.94 | 0.23 | 0.23 |
| – No Contrib Weighting | 0.07 | 0.41 | 0.09 | 0.09 |

## Citation
If you use this work, please cite:
```
@project{
  title = {Neuron-Guided Genre Refinement in LLM-Based Recommender
Systems using QRNCA},
  author = {Susheel Verma},
  year = {2025},
  institution = {IIT Bhilai},
}
```

## Author
**Susheel Verma (P25CS004)**  
Department of Computer Science and Engineeing, IIT Bhilai
