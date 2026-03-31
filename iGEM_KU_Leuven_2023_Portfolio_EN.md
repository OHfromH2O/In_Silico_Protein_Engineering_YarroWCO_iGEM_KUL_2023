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
4. [Results](#4-results)
   - [4.1 Wet Lab Results](#41-wet-lab-results)
   - [4.2 Dry Lab Results](#42-dry-lab-results)
5. [BioBrick Parts Contribution](#5-biobrick-parts-contribution)
6. [Conclusions & Future Directions](#6-conclusions--future-directions)
7. [References](#7-references)
8. [👥 Team & Author](#-team--author)

---

## 1. Project Introduction

### Background: Why This Project?

Belgium produces approximately **88,000 metric tons** of Waste Cooking Oil (WCO) annually. Our project, **YarroWCO**, converts this waste into **Campesterol**, a **$10 billion** market value steroid drug precursor.

<div align="center">
  <img src="Figures/Figure 2. Current synthesis methods of steroidal active pharmaceutical ingredient synthesis.png" width="750" alt="Synthesis Methods">
  <br>
  <em><b>Figure 2.</b> Current synthesis methods vs. our proposed biosynthetic approach using WCO.</em>
</div>

### Core Concept

We aim to replace traditional extraction methods with **WCO-based biosynthesis** via the oleaginous yeast ***Yarrowia lipolytica***.

<div align="center">
  <img src="Figures/Figure 3. Metabolic pathways in Yarrowia. Reproduced under permission.png" width="600" alt="Metabolic Pathways">
  <br>
  <em><b>Figure 3.</b> Metabolic pathways in Yarrowia lipolytica, focusing on the Mevalonate pathway.</em>
</div>

---

## 2. Overview & Key Models

### Dry Lab Objectives

Our computational work integrated **structural biology** and **growth kinetics**.

<div align="center">
  <img src="Figures/dry lab introduction_methods.png" width="800" alt="Dry Lab Methods">
  <br>
  <em><b>Dry Lab Summary:</b> Four pillars of our computational approach.</em>
</div>

---

## 3. Experimental Design

### 3a. Engineering Cycle (DBTL)

#### Iteration 1: pET28 System
We initially utilized a **pET28 backbone** for biosurfactant (hydrophobin) expression.

<div align="center">
  <img src="Figures/Table 1. Hydrophobins used for.png" width="600" alt="Hydrophobin Table">
  <br>
  <em><b>Table 1.</b> Hydrophobin candidates screened for expression.</em>
</div>

<div align="center">
  <img src="Figures/Figure 3. pET28_AcGFP_MBSP1_060723..png" width="450" alt="pET28 Map">
  <br>
  <em><b>Figure 3.</b> Vector map of the pET28_AcGFP_MBSP1 construct.</em>
</div>

**Initial Test:**
The first iteration showed successful insert PCR but **backbone amplification challenges**.

<div align="center">
  <img src="Figures/Figure 4. Agarose gel showing the result of our first iteration of the DBTL cycle.png" width="450" alt="DBTL Gel 1">
  <br>
  <em><b>Figure 4.</b> First iteration agarose gel: Validation of AcGFP and HGFI fragments.</em>
</div>

#### Iteration 2: Transition to pET29-sfGFP
We optimized the workflow using **Gibson Assembly** and a **linker-sfGFP fusion system**.

<div align="center">
  <img src="Figures/Figure 7. Flowchart for intermediate plasmid assembly.png" width="800" alt="Assembly Flowchart">
  <br>
  <em><b>Figure 7.</b> Flowchart of intermediate plasmid assembly for protein expression.</em>
</div>

<div align="center">
  <img src="Figures/Figure 5. pET29_link_MBSP1_200723.png" width="400" alt="pET29 MBSP1">
  <img src="Figures/Figure 6. pET29_linker_sfGFP_200723_5547bp.png" width="400" alt="pET29 sfGFP">
  <br>
  <em><b>Figures 5 & 6.</b> Optimized vector maps for biosurfactant-sfGFP fusions.</em>
</div>

---

## 4. Results

### 4.1 Wet Lab Results

#### PCR & Colony Confirmation
Systematic validation of gene fragments and successful transformants.

<div align="center">
  <img src="Figures/Figure 1 Agarose gel of PCR amplified gBlocks.png" width="400" alt="gBlock PCR">
  <img src="Figures/Figure 14. Q5 PCR result 1= ladder, 2=HFBI, 3= HFBII, 4= MBSP1, 5=pBEVY, 6= MF.png" width="400" alt="Q5 PCR">
  <br>
  <em><b>Left:</b> PCR of gBlocks. <b>Right:</b> Q5 high-fidelity PCR results.</em>
</div>

<div align="center">
  <img src="Figures/Fig16_18.png" width="850" alt="Combined Colony PCR">
  <br>
  <em><b>Figures 16-18.</b> Representative colony PCR results verifying MBSP1, HFBI, and HFBII integration.</em>
</div>

#### Sequencing & SDS-PAGE
Confirmation of genetic fidelity and protein production yield.

<div align="center">
  <img src="Figures/Figure 6. Sequencing results for MBSP1, HFBI (natural sequence) and the HFBI.png" width="450" alt="Sequencing Results">
  <img src="Figures/Figure 8. Sequencing result for linker plasmid.png" width="450" alt="Linker Sequencing">
  <br>
  <em><b>Sequencing Data:</b> High-quality chromatograms confirming the sfGFP-linker-target reading frame.</em>
</div>

<div align="center">
  <img src="Figures/Figure 7. SDS-PAGE for MBSP1, HFBI (natural sequence) and HFBI (mutated sequence).png" width="400" alt="SDS-PAGE">
  <img src="Figures/Figure 9. GFP expression in E. coli.png" width="450" alt="GFP Tube">
  <br>
  <em><b>Protein Analysis:</b> SDS-PAGE showing higher yield for mutant HFBI (left) and visible GFP fluorescence in pellet (right).</em>
</div>

---

## 5. BioBrick Parts Contribution

We submitted standardized parts to the iGEM Registry to facilitate future surfactant research.

<div align="center">
  <img src="Figures/BBa_K4661015.png" width="800" alt="BioBrick BBa_K4661015">
  <br>
  <em><b>Part BBa_K4661015:</b> HFBI (mutant)-Linker-sfGFP cassette.</em>
</div>

<div align="center">
  <img src="Figures/스크린샷 2026-03-30 173808.png" width="600" alt="Primer Sequence">
  <br>
  <em>Validation primer sequences for Registry submission.</em>
</div>

---

## 6. Conclusions & Future Directions

### Summary of Wet Lab Activities

<div align="center">
  <img src="Figures/Figure 5. Summary of wet lab activities performed in E. coli.png" width="800" alt="Wet Lab Summary">
  <br>
  <em><b>Figure 5.</b> Schematic summary of experimental pipeline in E. coli.</em>
</div>

### Future Strategy: Promoter Engineering
We proposed a transition to a **"Marionette"** promoter system for tighter regulation.

<div align="center">
  <img src="Figures/Figure 10. Our idea for improving our promotor and ensuring inducible expression of our target protein.png" width="700" alt="Promoter Optimization">
  <br>
  <em><b>Figure 10.</b> Proposed optimization of leaky vs. tight inducible promoters.</em>
</div>

---

## 7. References

1. Du, H.X. et al. Engineering *Yarrowia lipolytica* for campesterol overproduction. *PLoS ONE* **11** (2016)

2. Zhang, Y. et al. Improved campesterol production in engineered *Yarrowia lipolytica* strains. *Biotechnol. Lett.* **39** (2017)

3. Jumper, J. et al. Highly accurate protein structure prediction with AlphaFold. *Nature* **596** (2021)

4. Mirdita, M. et al. ColabFold: making protein folding accessible to all. *Nat. Methods* **19** (2022)

5. Trott, O. & Olson, A.J. AutoDock Vina: Improving the speed and accuracy of docking with a new scoring function, efficient optimization, and multithreading. *J. Comput. Chem.* (2009)

6. Pettersen, E.F. et al. UCSF Chimera — A visualization system for exploratory research and analysis. *J. Comput. Chem.* **25** (2004)

7. Laskowski, R.A. & Swindells, M.B. LigPlot+: Multiple ligand-protein interaction diagrams for drug discovery. *J. Chem. Inf. Model.* **51** (2011)

8. Stierand, K., Maaß, P.C. & Rarey, M. Molecular complexes at a glance: Automated generation of two-dimensional complex diagrams. *Bioinformatics* **22** (2006)

9. Cock, P.J.A. et al. Biopython: Freely available Python tools for computational molecular biology and bioinformatics. *Bioinformatics* **25** (2009)

10. Bendl, J. et al. PredictSNP: Robust and Accurate Consensus Classifier for Prediction of Disease-Related Mutations. *PLoS Comput. Biol.* **10** (2014)

11. Schymkowitz, J. et al. The FoldX web server: An online force field. *Nucleic Acids Res.* **33** (2005)

12. Radusky, L.G. & Serrano, L. PyFoldX: enabling biomolecular analysis and engineering along structural ensembles. *Bioinformatics* **38** (2022)

13. Jun Cheng et al. Accurate proteome-wide missense variant effect prediction with AlphaMissense. *Science* **381**, eadg7492 (2023)

14. Leon, M. et al. A computational method for the investigation of multistable systems and its application to genetic switches. *BMC Syst. Biol.* **10** (2016)

15. Gardner, T.S., Cantor, C.R. & Collins, J.J. Construction of a genetic toggle switch in *Escherichia coli*. *Nature* **403** (2000)

16. Bonnet, J., Subsoontorn, P. & Endy, D. Rewritable digital data storage in live cells via engineered control of recombination directionality. *Proc. Natl Acad. Sci. USA* **109** (2012)

---

## 👥 Team & Author

<div align="center">
  <img src="Figures/YarroWCO.png" width="800" alt="iGEM KU Leuven 2023 Team">
  <br>
  <em><b>iGEM KU Leuven 2023 Team 'YarroWCO' at Arenberg Castle.</b></em>
</div>

<br>

<div align="center">
  [🌐 Official Wiki](https://2023.igem.wiki/kuleuven/) | [🔬 Project Description](https://2023.igem.wiki/kuleuven/description) | [📊 Model](https://2023.igem.wiki/kuleuven/model)
</div>
