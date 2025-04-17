## 🧬 AlphaFold from Scratch - Architecture Overview

This project implements a simplified version of DeepMind's **AlphaFold2** using PyTorch. The model predicts the 3D atomic structure of a protein from its amino acid sequence, optionally with multiple sequence alignments (MSAs).

---

### 🔧 Architecture Diagram

```text
Input: Amino Acid Sequence (+ Optional MSA)
      |
      V
+----------------------+
| Sequence Embedding   | → 1D Representation (per-residue)
+----------------------+
           |
           V
+----------------------+
| Pair Embedding       | → 2D Representation (residue pair features)
+----------------------+
           |
           V
+==============================+
||         Evoformer         ||
||  - MSA Attention (optional)||
||  - Pairwise Triangle Ops   ||
||  - Self-Attention & FFN    ||
+==============================+
           |
           V
+----------------------+
| Structure Module     | → Predict 3D structure
| - Invariant Point Attention
| - Torsion Angle Head
| - Backbone Reconstruction
+----------------------+
           |
           V
Output: 3D coordinates (N, CA, C, O atoms)

```

---

### 🧩 Component Breakdown

| Module              | Description |
|---------------------|-------------|
| `sequence_tokenizer.py` | Tokenizes amino acid sequences into indices |
| `dataset.py` | Parses FASTA + PDB data, extracts coordinates |
| `sequence_embedding.py` | Embeds amino acids and adds positional encodings |
| `pair_embedding.py` | Initializes 2D residue-pair features |
| `evoformer.py` | Core of the model – processes sequence and pair features through triangle attention and multiplication |
| `structure_module.py` | Uses invariant point attention to predict final 3D structure |
| `losses.py` | Includes FAPE, distogram loss, and torsion loss |
| `train.py` | Training loop with checkpointing and logging |
| `visualize_predictions.ipynb` | Visualizes predicted structures and distograms |

---

### 📦 Dependencies
- PyTorch
- BioPython (for FASTA/PDB handling)
- numpy, matplotlib
- (Optional) PyMOL / Py3Dmol for 3D visualization

---

### 📈 Roadmap
See [`CHECKLIST.md`](./CHECKLIST.md) for a week-by-week implementation plan.

---

### 🧪 Notes
This implementation is educational and intentionally simplified. The full AlphaFold2 model includes template processing, recycling, and more complex loss functions, which may be optionally added in future iterations.

---
