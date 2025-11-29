# Compensation-Gap-Marriage-Model

**Code**: https://github.com/Republic1024/Compensation-Gap-Marriage-Model

### Unifying Mate Selection and Limit Order Books through State-Machine Dynamics
### Code Release for: *Why Compensation Cannot Close Gaps: A Computational Model of Marriage Markets with Internal Preference Differentials*

---

## 📌 Overview

This repository contains the full simulation code, agent-based models, and visualization pipeline for the paper:

**“Why Compensation Cannot Close Gaps: A Computational Model of Marriage Markets with Internal Preference Differentials”**

The project proposes a unified computational framework where **marriage markets** are modeled not as price-mediated exchanges, but as **argmax-driven matching systems** under geometric constraints. We map social dynamics to microstructure concepts:

- **Internal Ideal ($V_{\text{uncond}}$)** → `Ask Price` (Anchor)
- **Reachable Reality ($V_{\text{reach}}$)** → `Best Bid` (Liquidity)
- **$\Delta V$ Gap** → Structural **Bid-Ask Spread**
- **Regret** → Execution **Slippage**
- **Settling** → Threshold-decay crossing event ($T(t)$)

The framework demonstrates that **linear compensation cannot close structural preference gaps**, unless it triggers a **categorical identity shift** (Identity Collapse).

---

## 🔍 Core Concepts

### **1. The Gini Cone & Liquidity Drought**
- **Structure**: Social status is modeled as a conical distribution (derived from Lorenz Curve derivatives).
- **Constraint**: As status $h$ increases, reachable volume shrinks super-linearly
- **Consequence**: High-tier agents face a geometric **liquidity drought**, forcing "downward matching" despite high attributes.

### **2. Theorem 1 — Compensation Immunity**
Compensation $C$ is additive, but ranking is ordinal. The effective utility is modeled as:

$$
U_{\text{effective}} = V_{\text{intrinsic}} + \min(\epsilon \cdot C, C_{\text{cap}})
$$

**Key Insight**:

- If $C < C^*$ (Identity Threshold) → **Rank invariant**. The compensation strategy is dominated.
- If $C \ge C^*$ → **Identity Reconstruction**. The agent moves to a new bucket.

### **3. Threshold Dynamics (The "Settling" Logic)**
Marriage is not a functional mapping $f(x)$, but a state transition triggered by time decay. Commitment occurs when:

$$
\theta = \frac{V_{\text{reachable}}}{V_{\text{uncond}}} \ge T(t)
$$

Where $T(t)$ is the agent's internal threshold, decaying with age and social pressure[cite: 228]. [cite_start]This explains why **settling** happens without satisfaction improving.

---

## 📁 Repository Structure

```text
Compensation-Gap-Marriage-Model/
│
├── exp1-5.py           # Main experiments (Sections 4.2–4.6)
├── exp1-5-Chinese.py   # Chinese commented version for local developers
├── simulation_results.png # Visualization of Settling, Clipping, and Regret
├── .gitignore
└── README.md
````

-----

## 📊 Experiments Included (Sections 4.2–4.6)

### **Experiment 1 — The Futility of Compensation**
Simulates a low-tier suitor offering max compensation ($C=500k$).
* **Result**: Match fails. $\Delta V$ persists due to utility clipping. Money cannot buy ordinal rank.

### **Experiment 2 — Threshold Decay (Settling)**
Simulates an agent aging from 24 to 32.
* **Result**: Match occurs at age 32 not because $\theta$ improved, but because $T(t)$ crashed. Settling is just consuming liquidity under time pressure.

### **Experiment 3 — Instant Commitment**
Simulates encountering a High-Tier ($V \approx V_{\text{uncond}}$) partner.
* **Result**: Instant state transition to `COMMIT`. High-value assets clear immediately.

### **Experiment 4 — Regional Invariance**
Compares High-Bride-Price Norms (Jiangsu) vs. Low-Norms (Guangdong).
* **Result**: **Ranking is invariant**. Norms shift intercepts but do not alter the Argmax result.

### **Experiment 5 — Post-Marriage Regret (Slippage)**
Simulates an external information shock (e.g., peer comparison) post-commitment.
* **Result**: $V_{\text{uncond}}$ spikes $\to$ $\theta$ crashes $\to$ Agent enters hidden **Regret State**. Regret is structural execution slippage.

-----

## 🎨 Visualization

The script generates `simulation_results.png`, reproducing the key figures from the paper:

1.  **Settling Dynamics**: Visualizes the crossing point of $\theta(t)$ and $T(t)$.
2.  **Compensation Clipping**: Shows the diminishing returns of $C$.
3.  **Slippage Bars**: Quantifies the structural regret post-match.

-----

## ▶️ How to Run

### **1. Install dependencies**

```bash
pip install numpy pandas matplotlib
```

### **2. Run the core simulation**

```bash
python exp1-5.py
```

*For Chinese comments, run `python exp1-5-Chinese.py` instead.*

-----

## 📚 Citation

If you use this framework or code, please cite:

```bibtex
@article{Wu2025Compensation,
  title={Why Compensation Cannot Close Gaps: A Computational Model of Marriage Markets with Internal Preference Differentials},
  author={Wu, Yao},
  year={2025}
}
```

-----

## 🧠 Philosophy Behind the Model

> **"Money is linear; Desire is ordinal."**

This project demonstrates that marriage markets are **limit order books** running on **greedy algorithms** with infinite refresh rates.

  - **$\Delta V$** is the structural spread that cannot be closed by liquidity ($C$).
  - **Happiness** is not about what you get ($V_{\text{reach}}$), but the ratio against what you imagine ($V_{\text{uncond}}$).
