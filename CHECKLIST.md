# AlphaFold from Scratch - Weekly Implementation Checklist

This is a structured weekly plan to build a simplified AlphaFold model using PyTorch.

---

<details>
<summary><strong>Week 1: Deep Dive + Data & Tokenizer</strong></summary>

- [ ] Read the AlphaFold2 paper (DeepMind) and OpenFold repo
- [ ] Create repo structure and `README.md` with architecture overview
- [ ] Implement `sequence_tokenizer.py`
  - [ ] `tokenize_sequence(seq)` → list of indices
  - [ ] `detokenize(indices)` → sequence string
- [ ] Implement `dataset.py`
  - [ ] Parse FASTA + PDB files
  - [ ] Extract N, CA, C coordinates
  - [ ] Normalize protein structure
  - [ ] Add dummy MSA loader stub

</details>

---

<details>
<summary><strong>Week 2: Embeddings & Representations</strong></summary>

- [ ] Implement `sequence_embedding.py`
  - [ ] Learnable amino acid embedding
  - [ ] Positional encodings
- [ ] Implement `pair_embedding.py`
  - [ ] Outer product of sequence embeddings
  - [ ] Relative positional encodings
- [ ] Write unit tests for embeddings
- [ ] Create a notebook to visualize embeddings and shapes

</details>

---

<details>
<summary><strong>Week 3–4: Evoformer Block</strong></summary>

- [ ] Implement triangle multiplication (`triangle_multiplication.py`)
  - [ ] Incoming + outgoing modules
- [ ] Implement triangle attention (`triangle_attention.py`)
  - [ ] Start + end modules
- [ ] Implement pair transition MLP
- [ ] Combine into `evoformer_block.py` with residuals & layer norms
- [ ] Stack multiple blocks into `evoformer.py`
- [ ] Write shape/unit tests for each block

</details>

---

<details>
<summary><strong>Week 5: Invariant Point Attention + Structure Module</strong></summary>

- [ ] Implement IPA (`ipa_attention.py`)
  - [ ] SE(3) point attention mechanism
- [ ] Implement `structure_module.py`
  - [ ] Convert pair features to torsion angles
  - [ ] Reconstruct 3D coordinates
- [ ] Visualize predicted backbone structure

</details>

---

<details>
<summary><strong>Week 6: Loss Functions + Metrics</strong></summary>

- [ ] Implement `losses.py`
  - [ ] FAPE (Frame Aligned Point Error)
  - [ ] L2 loss on atom positions
  - [ ] Distogram bin classification loss
  - [ ] Torsion angle loss
- [ ] Implement `metrics.py`
  - [ ] RMSD metric
  - [ ] Distogram accuracy metric

</details>

---

<details>
<summary><strong>Week 7: Training Pipeline</strong></summary>

- [ ] Implement `train.py`
  - [ ] Evoformer → Structure → Loss
  - [ ] Optimizer & learning rate scheduler
  - [ ] Checkpointing & resume
- [ ] Train on toy proteins (10–20 residues)
- [ ] Log training loss, RMSD, distogram samples

</details>

---

<details>
<summary><strong>Week 8: Evaluation & Visualization</strong></summary>

- [ ] Create `visualize_predictions.ipynb`
  - [ ] Plot predicted vs true backbone
  - [ ] Plot distogram predictions
- [ ] Compare predictions from multiple checkpoints
- [ ] Update `README.md` with:
  - [ ] Architecture diagram
  - [ ] Sample predictions
  - [ ] Final training curves

</details>

---

### ✅ Final Notes:
- Use [GitHub Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects) to track progress visually.
- Each module should have associated unit tests.
- Keep PRs small and well-documented.
