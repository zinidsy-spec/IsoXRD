# IsoXRD (v4.4)
**Lightweight Browser-Based XRD Phase Identification, Pseudo-Voigt Deconvolution & PO-Corrected RIR Quantification Notebook**  
**웹 브라우저 기반 X-선 회절(XRD) 상동정, Pseudo-Voigt 피크 분리 및 우선 배향성 보정 RIR 반정량 분석 노트**

[![Version](https://img.shields.io/badge/version-v4.4-a84a28.svg)](https://github.com/zinidsy-spec/IsoXRD)
[![License: MIT](https://img.shields.io/badge/License-MIT-1b4d3e.svg)](https://opensource.org/licenses/MIT)
[![Client-Side](https://img.shields.io/badge/Architecture-100%25_Client--Side_HTML%2FJS-1e40af.svg)](#)

---

## 🌐 Overview / 개요

**English**  
**IsoXRD** is a zero-installation, client-side web application designed for rapid X-ray diffraction (XRD) screening, displacement correction, semi-automated phase identification, and 100%-normalized semi-quantitative weight analysis (`Weight%`). Built with pure vanilla HTML/CSS/JavaScript and SVG rendering, it runs entirely in the browser without external paid libraries or proprietary databases.

**한국어**  
**IsoXRD**는 별도의 프로그램 설치나 유료 라이선스 없이 웹 브라우저에서 즉시 실행되는 XRD 회절 패턴 분석 및 반정량(`Weight%`) 웹 애플리케이션입니다. 순수 바닐라 HTML/CSS/JavaScript 및 벡터 SVG 엔진으로 구현되어 데이터가 외부 서버로 전송되지 않으며, 연구실의 일상적인 상동정 스크리닝과 논문용 고해상도 벡터 그래프 제작을 지원합니다.

---

## ✨ Key Features / 주요 기능

### 1. Multi-Format Data Loader & Stack Visualization / 다중 포맷 지원 및 스택 비교
* **Supported Formats:** `.xrdml` (with automatic $K\alpha_1$ wavelength metadata parsing), PANalytical HighScore `.txt` (tab-delimited multi-column exports), `.csv`, and `.xy`.
* **Stack & Single Modes:** Overlay multiple depth/core samples in a normalized vertical stack or inspect single spectra in detail with interactive zoom and cursor $2\theta / d$-spacing readout.
* **지원 포맷:** `.xrdml`(파장 메타데이터 자동 인식), HighScore `.txt`(9열 탭 구분 내보내기 파일), `.csv`, `.xy` 등 다양한 원시 회절 파일을 동시 드래그하여 스택(Stack) 형태로 비교할 수 있습니다.

### 2. Non-Linear Displacement Correction / 비선형 변위 보정 ($\Delta 2\theta = s_0 + s_1\cos\theta$)
* **Zero-Point & Sample Height Shift:** Simultaneously corrects goniometer zero-shift ($s_0$) and specimen height displacement ($s_1\cos\theta$) via constrained **Auto-Fit** or manual fine-tuning sliders.
* **영점 및 시료 높이 변위 보정:** 분말 시료 충진 높이 차이로 인한 비선형 회절각 밀림을 **[자동 보정 (Auto-Fit)]** 또는 미세 슬라이더로 정렬합니다.

### 3. Semi-Automated Residual-Peak Phase Suggestion & Suite Presets / 잔차 피크 기반 누적 상추천 및 프리셋
* **Additive Residual-Peak Suggestion (`+ 미설명 피크 상추가` / `+ Add Residual Phases`):** Preserves existing manual or preset phase selections while incrementally adding up to 3 candidate phases matching unassigned residual peaks (`◆`).
* **Geological Suite Presets:** One-click presets (`Carbonate / Speleothem`, `Calc-Silicate / Skarn`, `Clastic / Soil`) plus persistent custom suite saving (`+ 내 조합 저장`).
* **강제 자동화의 오류 방지:** 기존에 선택한 광물을 덮어쓰지 않고, 차트 상에 주황색 다이아몬드(`◆2θ°`)로 표시된 **미할당 피크**와 일치하는 후보 광물만 3종씩 점진적으로 추가합니다.

### 4. Adaptive-FWHM Pseudo-Voigt Deconvolution & Universal PO Attenuation / 피크 분리 및 우선 배향성 보정
* **Adaptive Local FWHM:** Estimates individual peak widths ($0.10^\circ\text{–}0.45^\circ$) rather than assuming a fixed width, separating overlapping tails (e.g., Calcite $29.40^\circ$ vs. Diopside $29.80^\circ$) via Non-Negative Least Squares (NNLS) coordinate descent.
* **Universal Preferred Orientation (PO) Auto-Attenuation (`PO×0.xx`):** Phase-agnostic attenuation factor derived from secondary reflection ($I_{\text{rel}} \ge 15\%$) consistency to prevent overestimation of cleavage/basal-oriented minerals (e.g., Dolomite, Biotite, Muscovite).
* **Inline RIR ($I/I_c$) Calibration:** Edit RIR factors per mineral directly in the quantification panel (persisted in `localStorage`) and inspect the fit residual curve ($I_{\text{obs}} - I_{\text{fit}}$).
* **범용 우선 배향성 자동 감쇠 및 개별 FWHM:** 특정 광물 하드코딩 없이 보조 피크 일관성을 검증해 벽개면/판상 배향성으로 주피크만 증폭된 광물을 자동 감쇠 보정하며, 광물별 실측 `RIR` 값을 화면에서 즉시 수정할 수 있습니다.

### 5. Publication-Ready Export & In-App SOP / 논문용 내보내기 및 내장 매뉴얼
* **Themes & Exports:** Switch between `Linen`, `Journal`, `Blueprint`, and `Publication B&W` modes; export high-resolution `PNG`, editable vector `SVG`, and UTF-8 BOM `CSV` summaries.
* **Built-in SOP & Changelog:** Accessible directly from the top header (`[사용법 / 업데이트]`) in both Korean and English.

---

## 📖 Standard Operating Procedure (SOP) / 표준 작업 절차

| Step | English Workflow | 한국어 작업 절차 |
| :--- | :--- | :--- |
| **1. Load** | Drag & drop `.xrdml`, HighScore `.txt`, `.csv`, or `.xy` files into **Panel 1**. | **1번 패널**에 분석할 XRD 원시 파일들을 동시 드래그하여 업로드합니다. |
| **2. Align** | Click **Auto-Fit** in **Panel 2** to align peaks via $\Delta 2\theta = s_0 + s_1\cos\theta$, then fine-tune $s_0/s_1$ sliders if needed. | **2번 패널**의 **[자동 보정]**으로 기준 스틱과 피크 위치를 정렬하고 필요시 슬라이더로 미세 조정합니다. |
| **3. Identify** | Select a geological preset in **Panel 3**, then click **+ Add Residual Phases** to incrementally match remaining `◆` peaks. | **3번 패널**에서 시료 유형별 프리셋을 누른 뒤, 남은 미할당(`◆`) 피크는 **[+ 미설명 피크 상추가]**로 보완합니다. |
| **4. Quantify** | Review 100%-normalized RIR `Weight%` and `PO×0.xx` badges; adjust inline `RIR` values if calibrated against lab standards. | 총합 100.0%로 정규화된 RIR `Weight%`와 `PO` 감쇠 계수를 확인하고, 필요시 광물별 `RIR` 수치를 보정합니다. |
| **5. Export** | Export `CSV` tables, `PNG` figures, or vector `SVG` graphics, and copy the citation from **Cite / DOI**. | **[엑셀 CSV]**, **[그림 PNG]**, **[벡터 SVG]**로 결과를 내보내고 **[인용 / DOI]**에서 서지 정보를 복사합니다. |

---

## 📋 Release Notes (Changelog) / 업데이트 로그

### **v4.4 (2026-11-17)**
* **EN:** Added a bilingual (KO/EN) `[SOP / Changelog]` modal in the top header for immediate access to the Standard Operating Procedure and release notes.
* **KO:** 상단 헤더에 한/영 전환이 연동되는 **[사용법 / 업데이트]** 모달을 추가하여 표준 작업 절차서(SOP)와 버전별 변경 이력을 즉시 확인할 수 있도록 개선했습니다.

### **v4.3 (2026-11-17)**
* **EN:** Introduced additive `[+ Add Residual Phases]` suggestion (adds up to 3 candidates matching unexplained peaks without overwriting active phases) and amber diamond markers (`◆2θ°`) for unassigned peaks.
* **KO:** 기존 선택을 덮어쓰지 않고 미설명 잔차 피크와 일치하는 후보 광물 3종씩 누적 추가하는 **[+ 미설명 피크 상추가]** 버튼과 미할당 피크 다이아몬드(`◆2θ°`) 마커를 도입했습니다.

### **v4.2 (2026-11-17)**
* **EN:** Added geological phase combination presets (`Carbonate / Speleothem`, `Calc-Silicate / Skarn`, `Clastic / Soil`) and custom suite persistence (`+ Save My Suite`).
* **KO:** 암석·퇴적물 유형별 광물 조합 프리셋 3종과 사용자 정의 조합 영구 저장(**[+ 내 조합 저장]**) 기능을 추가했습니다.

### **v4.1 (2026-11-17)**
* **EN:** Implemented universal Preferred Orientation (PO) auto-attenuation (`PO×0.xx`), adaptive per-peak FWHM estimation ($0.10^\circ\text{–}0.45^\circ$), and residual curve ($I_{\text{obs}} - I_{\text{fit}}$) visualization.
* **KO:** 광물 구분 없이 보조 피크 일관성을 검증하는 범용 우선 배향성(PO) 자동 감쇠 보정, 개별 피크 반치폭(FWHM) 측정 및 잔차 곡선 시각화를 추가했습니다.

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

> Yang, Y.-S. (2026). *IsoXRD: Lightweight Browser-Based XRD Phase Identification and Semi-Quantitative Carbonate Analysis Tool* (Version 4.4) [Computer software]. Zenodo. https://github.com/zinidsy-spec/IsoXRD

```bibtex
@software{Yang_IsoXRD_2026,
  author       = {Yang, Yun-Seok},
  title        = {{IsoXRD: Lightweight Browser-Based XRD Phase Identification and Semi-Quantitative Carbonate Analysis Tool}},
  month        = nov,
  year         = 2026,
  publisher    = {Zenodo},
  version      = {v4.4},
  url          = {[https://github.com/zinidsy-spec/IsoXRD](https://github.com/zinidsy-spec/IsoXRD)}
}
