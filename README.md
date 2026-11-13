# IsoXRD (v2.3)

**Lightweight, Browser-Based XRD Phase Identification & Semi-Quantitative Carbonate Analysis Tool**

🔗 **Live App:** https://zinidsy-spec.github.io/IsoXRD/

## ✨ Key Features
- **Zero Installation & Client-Side Processing:** Runs 100% locally in your web browser—no software installation or server data upload required (KO/EN bilingual UI).
- **Multi-Format Parser:** Supports PANalytical `.xrdml` files (including XML files with `.csv` extensions) as well as standard 2-column `.csv`, `.txt`, and `.xy` raw spectra.
- **Non-Linear Sample Displacement Correction ($\Delta 2\theta = s_0 + s_1\cos\theta$):** Automatically fits zero-point shift ($s_0$) and sample height displacement ($s_1\cos\theta$).
- **Multi-Phase Search-Match & Carbonate Ratio:** Identifies primary and secondary phases via residual peak scanning and estimates **Calcite / Aragonite semi-quantitative percentages (%)**.
- **Custom Mineral DB Manager:** Import peak tables directly from RRUFF/literature, capture peaks from active spectra, and share custom libraries via JSON.

## ⚖️ Data & License
All built-in reference mineral peak positions ($2\theta$, $d$-spacings, and $hkl$ indices) are public-domain crystallographic constants calculated via Bragg's law ($n\lambda = 2d\sin\theta$). Free to use and share within the lab without proprietary database restrictions.

---
*Related Project: [IsoCalib](https://zinidsy-spec.github.io/Stable-isocalib/) — Open-source stable isotope data reduction platform.*
