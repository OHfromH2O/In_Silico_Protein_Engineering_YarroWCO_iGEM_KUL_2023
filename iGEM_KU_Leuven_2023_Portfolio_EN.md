# 🧬 iGEM KU Leuven 2023 — YarroWCO

> **A synthetic biology project engineering *Yarrowia lipolytica* to produce campesterol — a key steroid drug precursor — using Waste Cooking Oil (WCO) as a carbon source.**

[![iGEM 2023](https://img.shields.io/badge/iGEM-2023-blue)](https://2023.igem.wiki/kuleuven/)
[![KU Leuven](https://img.shields.io/badge/KU%20Leuven-Team-003d6b)](https://2023.igem.wiki/kuleuven/team)
[![Best Model](https://img.shields.io/badge/Award-Best%20Model%20Nominee-gold)](https://2023.igem.wiki/kuleuven/model)

---

## 📋 Table of Contents

1. [Project Introduction](#1-project-introduction)
2. [Overview & Key Models](#2-overview--key-models)
3. [Experimental Design](#3-experimental-design)
   - [3a. Engineering Cycle (DBTL)](#3a-engineering-cycle-dbtl)
   - [3b. Experimental Protocols](#3b-experimental-protocols)
4. [Lab Notebooks](#4-lab-notebooks)
5. [Results](#5-results)
   - [5.1 Wet Lab Results](#51-wet-lab-results)
   - [5.2 Dry Lab Results](#52-dry-lab-results)
6. [BioBrick Parts Contribution](#6-biobrick-parts-contribution)
7. [Conclusions & Future Directions](#7-conclusions--future-directions)
8. [References](#8-references)

---

## 1. Project Introduction

### Background: Why This Project?

Belgium is renowned for its fried food culture; in 2021 alone, approximately 88,000 metric tons of Waste Cooking Oil (WCO) were generated. This project explores a high-value alternative to biodiesel by converting WCO into pharmaceutical precursors.

<div align="center">
  <img src="Figures/Figure 2. Current synthesis methods of steroidal active pharmaceutical ingredient synthesis.png" width="800" alt="Current synthesis methods">
  <br>
  <em><b>Figure 2.</b> Comparison of current steroid drug precursor extraction vs. our proposed biosynthetic approach.</em>
</div>

### Core Concept

We aim to replace traditional plant/animal extraction with WCO-based biosynthesis via *Y. lipolytica*.

<div align="center">
  <img src="Figures/Figure 3. Metabolic pathways in Yarrowia. Reproduced under permission.png" width="600" alt="Metabolic pathways in Yarrowia">
  <br>
  <em><b>Figure 3.</b> Metabolic pathways in Yarrowia lipolytica, focusing on the Mevalonate pathway for campesterol production.</em>
</div>

---

## 2. Overview & Key Models

> 📌 **iGEM 2023 Best Model Nominee** > Official model page: [https://2023.igem.wiki/kuleuven/model](https://2023.igem.wiki/kuleuven/model)

### Dry Lab Objectives Summary

Our computational work focused on four pillars: Enzyme screening, Growth modeling, Hydrophobin design, and Genetic switch logic.

<div align="center">
  <img src="Figures/dry lab introduction_methods.png" width="800" alt="Dry Lab Methods Summary">
  <br>
  <em><b>Dry Lab Summary:</b> Integration of structural bioinformatics and systems biology modeling.</em>
</div>

---

## 3. Experimental Design

### 3a. Engineering Cycle (DBTL)

#### Iteration 1: First Cloning Attempt in pET28

Initially, we designed 8 constructs using the pET28 backbone and AcGFP-linker-hydrophobin fusion.

<div align="center">
  <img src="Figures/Figure 3. pET28_AcGFP_MBSP1_060723..png" width="500" alt="pET28 Vector Map">
  <br>
  <em><b>Figure 3.</b> Vector map of pET28_AcGFP_MBSP1 used in the first DBTL cycle.</em>
</div>

**Build & Test:**
The initial PCR for the pET28 backbone failed, prompting a transition to a new cloning strategy.

<div align="center">
  <img src="Figures/Figure 4. Agarose gel showing the result of our first iteration of the DBTL cycle.png" width="450" alt="First DBTL Agarose Gel">
  <br>
  <em><b>Figure 4.</b> Agarose gel result: Lane 2 (pET28 backbone) failure vs. Lane 4/5 (inserts) success.</em>
</div>

---

## 5. Results

### 5.1 Wet Lab Results

#### PCR Amplification of gBlocks
Successful amplification was achieved for various hydrophobin inserts (MBSP1, HFBI, HFBII, HGFI).

<div align="center">
  <img src="Figures/Figure 1 Agarose gel of PCR amplified gBlocks.png" width="450" alt="PCR gBlocks">
  <br>
  <em><b>Figure 1.</b> High-fidelity PCR results for diverse hydrophobin gBlock fragments.</em>
</div>

#### Colony PCR for Gibson Assembly
Confirmation of successful transformants for MBSP1 and HFBI (Natural/Mutant).

<div align="center">
  <img src="Figures/Figure 2. Colony PCR for Gibson assemblies of MBSP1.png" width="400" alt="Colony PCR MBSP1">
  <img src="Figures/Figure 3. Colony PCR for Gibson assemblies of HFBI (natural sequence).png" width="400" alt="Colony PCR HFBI">
  <br>
  <em><b>Figure 2 & 3.</b> Successful colony PCR bands indicating correct insert integration.</em>
</div>

#### Summary of Colony PCR results (HFBII, HFBI, MBSP1)
Systematic screening across multiple constructs to verify positive clones.

<div align="center">
  <img src="Figures/Fig16_18.png" width="900" alt="Combined Colony PCR Results">
  <br>
  <em><b>Figure 16-18.</b> Representative gels for HFBII (left), HFBI (middle), and MBSP1 (right) colony PCRs.</em>
</div>

---

## 6. BioBrick Parts Contribution

We successfully submitted **BBa_K4661015** to the iGEM Registry, providing a standardized part for hydrophobin-sfGFP fusion expression.

<div align="center">
  <img src="Figures/BBa_K4661015.png" width="800" alt="BioBrick BBa_K4661015">
  <br>
  <em><b>Part BBa_K4661015:</b> HFBI (mutant)-Linker-sfGFP expression cassette.</em>
</div>

---

## 7. Conclusions & Future Directions

### Key Achievements
- **Wet Lab:** Expressed MBSP1 and HFBI in *E. coli*; verified that Cys→Ser mutations enhance yield.
- **Dry Lab:** Completed molecular docking/MD for 10 DHCR7 enzymes; established *Y. lipolytica* growth models.

---

<div align="center">

**iGEM KU Leuven 2023 | YarroWCO**

[🌐 Official Wiki](https://2023.igem.wiki/kuleuven/) | [🔬 Description](https://2023.igem.wiki/kuleuven/description) | [📊 Model](https://2023.igem.wiki/kuleuven/model) | [📋 Results](https://2023.igem.wiki/kuleuven/results)

</div>
