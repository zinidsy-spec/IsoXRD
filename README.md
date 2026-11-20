# IsoXRD (v4.6)
**Lightweight Browser-Based XRD Phase Identification, Pseudo-Voigt Deconvolution & PO-Corrected RIR Quantification Workbench**  
**웹 브라우저 기반 X-선 회절(XRD) 상동정, Pseudo-Voigt 피크 분리 및 우선 배향성 보정 RIR 반정량 분석 워크벤치**

[![Version](https://img.shields.io/badge/version-v4.6-a84a28.svg)](https://github.com/zinidsy-spec/IsoXRD)
[![License: MIT](https://img.shields.io/badge/License-MIT-1b4d3e.svg)](https://opensource.org/licenses/MIT)
[![Client-Side](https://img.shields.io/badge/Architecture-100%25_Client--Side_HTML%2FJS-1e40af.svg)](#)

---

## 🌐 Overview / 개요

**English**  
**IsoXRD** is a zero-installation, client-side web application designed for rapid X-ray diffraction (XRD) screening, displacement correction, semi-automated phase identification, and 100%-normalized semi-quantitative weight analysis (`Weight%`). Built with pure vanilla HTML/CSS/JavaScript and SVG rendering, it runs entirely in the browser without external paid libraries or proprietary databases.

**한국어**  
**IsoXRD**는 별도의 프로그램 설치나 유료 라이선스 없이 웹 브라우저에서 즉시 실행되는 XRD 회절 패턴 분석 및 반정량(`Weight%`) 웹 애플리케이션입니다. 순수 바닐라 HTML/CSS/JavaScript 및 벡터 SVG 엔진으로 구현되어 데이터가 외부 서버로 전송되지 않으며, 스펙트럼 중심의 미니멀 워크스페이스를 통해 정밀한 회절 피크 판독과 논문용 고해상도 벡터 그래프 제작을 지원합니다.

---

## ✨ Key Features / 주요 기능

### 1. Spectrum-First Minimalist Workbench / 스펙트럼 중심 미니멀 워크스페이스
* **Expansive Diffraction Canvas:** Eliminates bulky top KPI banners by integrating inline status chips into the chart toolbar, providing a tall (`560px` default) diffraction stage with **`[⛶ Expand Chart]`** full-width toggle and collapsible bottom data tables.
* **Slim 3-Tab Sidebar (`310px`):** Organizes controls into three clean tabs—**`1. Samples/Quant`**, **`2. Minerals/Suite`**, and **`3. Align/Peaks`**—for distraction-free analysis across four themes (`Linen`, `Swiss`, `Blueprint`, `Obsidian`).
* **그래프 중심 인터페이스:** 상단 KPI 박스를 차트 툴바의 인라인 요약 칩으로 통합하고 좌측 제어 패널을 3개 탭(`1. 시료/정량`, `2. 광물/프리셋`, `3. 보정/피크`)으로 슬림화하여 회절 스펙트럼이 화면의 75~80%를 차지하도록 설계했습니다.

### 2. Multi-Format Data Loader & Stack Visualization / 다중 포맷 지원 및 스택 비교
* **Supported Formats:** `.xrdml` (with automatic $K\alpha_1$ wavelength metadata parsing), PANalytical HighScore `.txt` (tab-delimited multi-column exports), `.csv`, and `.xy`.
* **Stack & Single Modes:** Overlay multiple depth/core samples in a normalized vertical stack or inspect single spectra in detail with interactive zoom and cursor $2\theta / d$-spacing readout.

### 3. Non-Linear Displacement Correction / 비선형 변위 보정 ($\Delta 2\theta = s_0 + s_1\cos\theta$)
* **Zero-Point & Sample Height Shift:** Simultaneously corrects goniometer zero-shift ($s_0$) and specimen height displacement ($s_1\cos\theta$) via constrained **Auto-Fit** or manual fine-tuning sliders in Tab 3.

### 4. Semi-Automated Residual-Peak Phase Suggestion & Suite Presets / 잔차 피크 기반 누적 상추천 및 프리셋
* **Additive Residual-Peak Suggestion (`+ 미설명 피크 상추가` / `+ Add Residual Phases`):** Preserves existing manual or preset phase selections while incrementally adding up to 3 candidate phases matching unassigned residual peaks (`◆`).
* **Geological Suite Presets:** One-click presets (`Carbonate`, `Calc-Silicate`, `Clastic/Soil`) plus persistent custom suite saving (`+ Save Suite`).

### 5. Adaptive-FWHM Pseudo-Voigt Deconvolution & Universal PO Attenuation / 피크 분리 및 우선 배향성 보정
* **Adaptive Local FWHM:** Estimates individual peak widths ($0.10^\circ\text{–}0.45^\circ$) rather than assuming a fixed width, separating overlapping tails via Non-Negative Least Squares (NNLS) coordinate descent.
* **Universal Preferred Orientation (PO) Auto-Attenuation (`PO×0.xx`):** Phase-agnostic attenuation factor derived from secondary reflection ($I_{\text{rel}} \ge 15\%$) consistency to prevent overestimation of cleavage/basal-oriented minerals (e.g., Dolomite, Biotite, Muscovite).
* **Inline RIR ($I/I_c$) Calibration:** Edit RIR factors per mineral directly in Tab 1 (persisted in `localStorage`) and inspect the fit residual curve ($I_{\text{obs}} - I_{\text{fit}}$).

---

## 📖 Standard Operating Procedure (SOP) / 표준 작업 절차

| Step | English Workflow | 한국어 작업 절차 |
| :--- | :--- | :--- |
| **1. Load & Quant** | Drag & drop `.xrdml`, HighScore `.txt`, `.csv`, or `.xy` files into **Tab 1 (`1. Samples/Quant`)** and review 100%-normalized RIR `Weight%`. | **1번 탭(`1. 시료/정량`)**에 XRD 원본 파일들을 동시 드래그하여 올리고 총합 100.0% 기준 RIR `Weight%`를 확인합니다. |
| **2. Presets & DB** | Open **Tab 2 (`2. Minerals/Suite`)** to select a geological suite preset or toggle individual mineral pills. | **2번 탭(`2. 광물/프리셋`)**에서 시료 유형별 프리셋을 선택하거나 개별 광물 알약을 클릭해 후보군을 설정합니다. |
| **3. Residual Match** | Return to **Tab 1** and click **+ Add Residual Phases** to incrementally match remaining `◆` unassigned peaks. | 차트에 주황색 다이아몬드(`◆`) 미할당 피크가 남으면 **1번 탭**의 **[+ 미설명 피크 상추가]**로 보완합니다. |
| **4. Align & Expand** | Use **Tab 3 (`3. Align/Peaks`)** for **Auto-Fit** ($\Delta 2\theta = s_0 + s_1\cos\theta$), and toggle **⛶ Expand Chart** for full-width inspection. | **3번 탭(`3. 보정/피크`)**의 **[자동 보정]**으로 위치를 정렬하고 **[⛶ 그래프 확대]**로 피크를 정밀 판독합니다. |
| **5. Export & Cite** | Export `CSV` tables, `PNG` figures, or vector `SVG` graphics from the top header, and copy the citation from **Cite / DOI**. | 상단 헤더에서 **CSV / PNG / SVG**로 결과를 내보내고 **[인용 / DOI]**에서 서지 정보를 복사합니다. |

---

## 📋 Release Notes (Changelog) / 업데이트 로그

### **v4.6 (2026-11-20) — Spectrum-First Minimalist Workbench**
* **EN:** Removed bulky top KPI cards and consolidated key metrics into inline chart toolbar chips; compressed the left sidebar into 3 clean tabs (`1. Samples/Quant`, `2. Minerals/Suite`, `3. Align/Peaks`) and added `[⛶ Expand Chart]` and `[▼ Collapse Table]` toggles to maximize spectrum display area.
* **KO:** 상단 4칸 KPI 박스를 제거해 핵심 지표를 차트 툴바 인라인 칩으로 통합하고, 좌측 사이드바를 3개 컴팩트 탭(`310px`)으로 압축했으며 `[⛶ 그래프 확대]` 및 `[▼ 표 접기]` 토글을 추가해 회절 스펙트럼 영역을 대폭 확장했습니다.

### **v4.4 – v4.5 (2026-11-17 ~ 2026-11-20)**
* **EN:** Added bilingual (KO/EN) `[SOP / Changelog]` modal in the top header, hardened local `file://` boot sequence, and introduced 4 editorial themes (`Linen`, `Swiss`, `Blueprint`, `Obsidian`).
* **KO:** 상단 헤더에 한/영 전환이 연동되는 **[사용법 / 업데이트]** 모달을 추가하고, 로컬(`file://`) 부팅 안정화 및 4종 테마(`Linen`, `Swiss`, `Blueprint`, `Obsidian`) 시스템을 도입했습니다.

### **v4.3 (2026-11-17)**
* **EN:** Introduced additive `[+ Add Residual Phases]` suggestion (adds up to 3 candidates matching unexplained peaks without overwriting active phases) and amber diamond markers (`◆2θ°`) for unassigned peaks.
* **KO:** 기존 선택을 덮어쓰지 않고 미설명 잔차 피크와 일치하는 후보 광물 3종씩 누적 추가하는 **[+ 미설명 피크 상추가]** 버튼과 미할당 피크 다이아몬드(`◆2θ°`) 마커를 도입했습니다.

### **v4.1 – v4.2 (2026-11-17)**
* **EN:** Implemented universal Preferred Orientation (PO) auto-attenuation (`PO×0.xx`), adaptive per-peak FWHM estimation ($0.10^\circ\text{–}0.45^\circ$), residual curve ($I_{\text{obs}} - I_{\text{fit}}$) overlay, and geological phase suite presets.
* **KO:** 광물 구분 없이 보조 피크 일관성을 검증하는 범용 우선 배향성(PO) 자동 감쇠 보정, 개별 피크 반치폭(FWHM) 측정, 잔차 곡선 시각화 및 광물 조합 프리셋을 추가했습니다.

### **v4.0 & v3.6 – v3.8 (2026-11-16)**
* **EN:** Built Pseudo-Voigt profile deconvolution (NNLS), 100%-normalized multi-phase RIR `Weight%` calculator, inline RIR overrides, HighScore 9-column `.txt` parser, and `.xrdml` wavelength auto-detection.
* **KO:** Pseudo-Voigt 프로파일 디컨볼루션, 다중 광물 RIR 100% 정규화 반정량 엔진, 광물별 인라인 RIR 수정, HighScore 탭 구분 `.txt` 파서 및 `.xrdml` 파장 자동 인식을 구현했습니다.

---

## ⚖️ License & Data Attribution / 라이선스 및 데이터 출처

* **Software License:** Released under the **MIT License**. All smoothing, baseline estimation, Pseudo-Voigt deconvolution, and RIR normalization routines are implemented using standard open mathematical formulations with zero proprietary dependencies.
* **Crystallographic Reference Data:** Built-in reference peak positions ($2\theta, d, hkl$) and approximate $I/I_c$ ratios are compiled from open crystallographic literature and public databases (**Crystallography Open Database [COD]** and **RRUFF Project**). No proprietary ICDD PDF card numbers or copyrighted commercial databases are included.

---

## 📚 How to Cite / 인용 방법

If you use **IsoXRD** in your research or publication, please cite:

> Yang, Y.-S. (2026). *IsoXRD: Lightweight Browser-Based XRD Phase Identification and Semi-Quantitative Carbonate Analysis Tool* (Version 4.6) [Computer software]. Zenodo. https://github.com/zinidsy-spec/IsoXRD

```bibtex
@software{Yang_IsoXRD_2026,
  author       = {Yang, Yun-Seok},
  title        = {{IsoXRD: Lightweight Browser-Based XRD Phase Identification and Semi-Quantitative Carbonate Analysis Tool}},
  month        = nov,
  year         = 2026,
  publisher    = {Zenodo},
  version      = {v4.6},
  url          = {[https://github.com/zinidsy-spec/IsoXRD](https://github.com/zinidsy-spec/IsoXRD)}
}
