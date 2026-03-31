
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
   - [4a. DHCR7 Enzyme Screening](#4a-dhcr7-enzyme-screening-dry-lab)
   - [4b. Hydrophobin Design](#4b-hydrophobin-design-dry-lab)
   - [4c. Genetic Switch](#4c-genetic-switch-dry-lab)
   - [4d. Molecular Dynamics Simulation Protocol](#4d-molecular-dynamics-simulation-protocol)
5. [Results](#5-results)
6. [BioBrick Parts Contribution](#6-biobrick-parts-contribution)
7. [Conclusions & Future Directions](#7-conclusions--future-directions)
8. [References](#8-references)
9. [👥 Team & Author](#9-team--author)

---

## 1. Project Introduction

### Background: Why This Project?

Over **two billion tons of waste cooking oil (WCO)** were produced globally in 2016 alone. Belgium is renowned for its fried food culture; in 2021, approximately 88,000 metric tons of WCO were generated in the country. Just one liter of WCO can contaminate over one million liters of water.

The EU currently converts WCO into biodiesel (UCOME), but combustion still releases CO₂. This project explores a higher-value alternative.

<div align="center">
  <img src="Figures/Figure 2. Current synthesis methods of steroidal active pharmaceutical ingredient synthesis.png" width="750" alt="Synthesis Methods">
  <br>
  <em><b>Figure 2.</b> Current synthesis methods vs. our proposed biosynthetic approach using WCO.</em>
</div>

### Core Concept

```text
Waste Cooking Oil (WCO)
        │
        ▼  [Yarrowia lipolytica + biosurfactants]
        │
        ▼  Uptake and metabolism as carbon source
        │
        ▼  [Mevalonate pathway + DHCR7 enzyme]
        │
        ▼
Campesterol (key pharmaceutical intermediate)
        │
        ▼  Chemical / biological conversion
        │
        ▼
Steroid drugs (~$10 billion market, >1 million tons/year)
````

  - **Steroid drug market**: \>1 million tons produced annually; market value \~$10 billion USD
  - **Campesterol**: critical precursor for corticosteroids, sex hormones, and other steroids
  - **Core challenge**: campesterol currently relies on plant/animal extraction → replace with WCO-based biosynthesis via *Y. lipolytica*

\<div align="center"\>
\<img src="Figures/Figure 3. Metabolic pathways in Yarrowia. Reproduced under permission.png" width="600" alt="Metabolic Pathways"\>
<br>
\<em\>\<b\>Figure 3.\</b\> Metabolic pathways in Yarrowia lipolytica, focusing on the Mevalonate pathway.\</em\>
\</div\>

### Project Structure

| Component | Scope | Team |
|-----------|-------|------|
| **Wet Lab** | Expression vector construction for biosurfactants (hydrophobins); validation in *E. coli*; *Y. lipolytica* growth modelling | Wet lab team |
| **Dry Lab** | DHCR7 enzyme screening; hydrophobin design; genetic switch; growth model construction | Dry lab team |

-----

## 2\. Overview & Key Models

> 📌 **iGEM 2023 Best Model Nominee** \> Official model page: [https://2023.igem.wiki/kuleuven/model](https://2023.igem.wiki/kuleuven/model)

\<div align="center"\>
\<img src="Figures/dry lab introduction\_methods.png" width="800" alt="Dry Lab Methods"\>
<br>
\<em\>\<b\>Dry Lab Summary:\</b\> Four pillars of our computational approach.\</em\>
\</div\>

### 2.1 Three Core Dry Lab Objectives

#### ① DHCR7 Enzyme Screening

The final step in campesterol biosynthesis requires delta-7-sterol reductase (DHCR7), which is absent in *Y. lipolytica*. We performed *in silico* screening of 10 DHCR7 candidate enzymes from different organisms via molecular docking and molecular dynamics (MD) simulations.

**Screened organisms (10 species)**:

| Organism | Structure Source |
|----------|-----------------|
| *Rattus norvegicus* | PDB (CSM) |
| *Mus musculus* | PDB (CSM) |
| *Homo sapiens* | PDB (CSM) |
| *Danio rerio* | PDB (CSM) |
| *Xenopus laevis* | PDB (CSM) |
| *Xenopus tropicalis* | PDB (CSM) |
| *Bos taurus* | PDB (CSM) |
| *Arabidopsis thaliana* | PDB (CSM) |
| *Gallus gallus* | **AlphaFold3 prediction** |
| *Waddlia chondrophila* | **AlphaFold3 prediction** |

> **Assumption & Limitation**: DHCR7 is a transmembrane protein with no experimentally determined 3D structure. All structures are computationally predicted (CSM or AlphaFold3). Results are therefore provisional and require experimental validation.

#### ② *Yarrowia lipolytica* Growth Model

  - Modelled using R packages `biogrowth` and `growthrates`, supplemented by Python libraries
  - Compared growth on glucose vs. oil-based media
  - Growth phases captured: lag, exponential, and stationary

#### ③ Hydrophobin Design (pI Optimisation)

  - Starting protein: HFBI (PDB: 2FZ6, 75 aa, 2× Lys + 1× Arg)
  - Strategy: substitute Lys/Arg with Glu/Asp to lower theoretical isoelectric point (pI)
  - Objective: improve emulsification efficiency at the acidic pH preferred by *Y. lipolytica*

### 2.2 Computational Tools Summary

| Analysis | Tool |
|----------|------|
| Structure prediction | AlphaFold Colab, ColabFold |
| Molecular docking | AutoDock Vina 1.1.2 (UCSF Chimera) |
| MD simulation | AMBER22 (GPU: NVIDIA RTX3080ti) |
| Interaction visualisation | PoseView, LigPlot+ |
| pI calculation | BioPython |
| Mutation impact prediction | PredictSNP |
| Growth modelling | R (`biogrowth`, `growthrates`), Python |

-----

## 3\. Experimental Design

### 3a. Engineering Cycle (DBTL)

**Three complete DBTL iterations** were performed in *E. coli*:

```text
Design ──► Build ──► Test ──► Learn
  ▲                              │
  └──────────────────────────────┘
```

#### Iteration 1: First Cloning Attempt in pET28

**Design**

  - pET28 backbone + AcGFP-linker-hydrophobin fusion constructs
  - Screened biosurfactants: HFBI, HFBII, HGFI, MBSP1, and cysteine-mutant variants (8 constructs total)
  - Golden Gate cloning strategy

\<div align="center"\>
\<img src="Figures/Table 1. Hydrophobins used for.png" width="600" alt="Hydrophobin Table"\>
<br>
\<em\>\<b\>Table 1.\</b\> Hydrophobin candidates screened for expression.\</em\>
\</div\>

\<div align="center"\>
\<img src="Figures/Figure 3. pET28\_AcGFP\_MBSP1\_060723..png" width="450" alt="pET28 Map"\>
<br>
\<em\>\<b\>Figure 3.\</b\> Vector map of the pET28\_AcGFP\_MBSP1 construct.\</em\>
\</div\>

**Build & Test**

  - pET28 backbone amplified with Q5 High-Fidelity 2× Master Mix (NEB); 50 µL reaction, 10 ng plasmid template
  - gBlock inserts amplified with Taq DNA Polymerase (NEB); 5 ng gBlock DNA
  - AcGFP and HGFI\_full\_mutated PCR successful; pET28 backbone PCR failed

\<div align="center"\>
\<img src="Figures/Figure 4. Agarose gel showing the result of our first iteration of the DBTL cycle.png" width="450" alt="DBTL Gel 1"\>
<br>
\<em\>\<b\>Figure 4.\</b\> First iteration agarose gel: Validation of AcGFP and HGFI fragments.\</em\>
\</div\>

**Learn**

  - Backbone amplification failure investigated → transition to a new cloning strategy

#### Iterations 2 & 3: Transition to pET29-linker-sfGFP System

**Design**

  - pET29-sfGFP backbone + 21 bp linker (SGGSGGS) + hydrophobin fusion
  - Switched from Golden Gate (BsaI-based) to Gibson Assembly
  - Final targets: MBSP1, HFBI (natural/mutant), HFBII (mutant), HGFI series

\<div align="center"\>
\<img src="Figures/Figure 7. Flowchart for intermediate plasmid assembly.png" width="800" alt="Assembly Flowchart"\>
<br>
\<em\>\<b\>Figure 7.\</b\> Flowchart of intermediate plasmid assembly for protein expression.\</em\>
\</div\>

\<div align="center"\>
\<img src="Figures/Figure 5. pET29\_link\_MBSP1\_200723.png" width="400" alt="pET29 MBSP1"\>
\<img src="Figures/Figure 6. pET29\_linker\_sfGFP\_200723\_5547bp.png" width="400" alt="pET29 sfGFP"\>
<br>
\<em\>\<b\>Figures 5 & 6.\</b\> Optimized vector maps for biosurfactant-sfGFP fusions.\</em\>
\</div\>

**Key Build Conditions**

```text
Gibson Assembly:
  - Plasmid backbone: 50 ng
  - Insert ratio: 1:4 (backbone:insert)
  - NEBuilder® HiFi DNA Assembly Master Mix (NEB)
  - Incubation: 15 min (short fragments) or 1 h (long fragments) at 50°C

Transformation:
  - Host: DH10-beta chemically competent E. coli
  - Heat shock: 42°C, 30 sec
  - Recovery: SOC medium 500 µL, 37°C, 1 h
  - Selection: kanamycin plates
```

**Test**

  - Colony PCR followed by Macrogen Sanger sequencing
  - Confirmed: MBSP1, HFBI (natural), HFBI (mutant), HFBII (mutant)

-----

### 3b. Experimental Protocols

#### Plasmid Extraction

```text
Strains: E. coli DH10-beta carrying pET28, pET29, or pBEVY plasmids
Medium: LB broth + antibiotic (ampicillin 100 µg/mL or kanamycin 50 µg/mL)
Culture: 37°C, overnight (<18 h)
Centrifugation: 4,000 × g, 10 min
Kit: GeneJET Plasmid Miniprep Kit (ThermoFisher Scientific)
```

#### PCR Cycling Conditions

**Q5 Polymerase (backbone amplification)**
*(Protocol details retained in full codebase)*

**Taq Polymerase (insert amplification)**
*(Protocol details retained in full codebase)*

#### Protein Expression

```text
Strain: E. coli BL21
Pre-culture: LB broth + kanamycin 50 µg/mL, 3 mL, overnight
Main culture: LB broth, 50 mL; IPTG induction at OD = 0.5 (final concentration: 400 µM)
Expression: 37°C, 3 h in the presence of IPTG
Harvest: 4,000 × g, 20 min
```

#### Protein Purification

```text
Resuspension: 1× PBS
Sonication: 15 × 30 sec pulses (30 sec intervals)
Centrifugation: 16,000 × g, 20 min (collect supernatant)
Purification: HisPur Ni-NTA Resin (ThermoFisher Scientific)
              Manufacturer protocol followed, with 1 h additional shaking in resin
```

#### *Yarrowia lipolytica* Growth Curve

```text
Inoculation: single colony → YPD 3 mL, overnight, 30°C, 200 rpm
Starting OD: diluted to 0.1
Carbon source conditions:
  - Oil medium:     1.85 mL oil + 48.15 mL YP    (3.7% v/v)
  - Glucose medium: 6.25 mL 40% glucose + 43.75 mL YP (5% w/v)
Measurement: OD every 2 h over 60 h total
Replicates: 2 per condition
```

-----

## 4\. Lab Notebooks

### 4a. DHCR7 Enzyme Screening (Dry Lab)

**Period**: 1 July 2023 – 9 September 2023

#### I. Preparation (1/7 – 20/7)

**Motivation** The final step of the campesterol biosynthesis pathway requires delta-7-sterol reductase (DHCR7), which is not natively present in *Y. lipolytica*. Based on literature (Du et al. 2016; Zhang et al. 2017), 10 DHCR7 candidates from different organisms were selected for screening.

#### II. Structure Prediction (28/7 – 2/8)

DHCR7 structures for *Gallus gallus* and *Waddlia chondrophila* were not deposited in the PDB and were therefore predicted using AlphaFold Colab & ColabFold.

#### III. Molecular Docking (1/8 – 15/9)

**Tool**: AutoDock Vina (UCSF Chimera)  
**Protocol**: provided by Prof. Jeremy Harvey  
**Ligands**: NADPH, ergosta-5,7-dienol (downloaded from PubChem)

#### IV. Molecular Dynamics Simulations (19/9 – 9/9)

**Software**: AMBER22  
**Hardware**: NVIDIA RTX3080ti GPU  
**MD Pipeline**: Energy minimisation → Heating → Density equilibration → Equilibration → Production (20 ns total).

-----

### 4b. Hydrophobin Design (Dry Lab)

**Period**: 1 August 2023 – 8 September 2023

#### Design Rationale

Hydrophobins exhibit optimal emulsification activity at alkaline pH (\~9), but *Y. lipolytica* prefers acidic conditions. **Goal: engineer an HFBI variant with a lower pI that retains emulsification activity at acidic pH.**

#### I. Sequence Generation (22/8 – 24/8)

**Strategy**: Use BioPython to calculate protein pI, enumerate all combinations of Lys/Arg → Glu/Asp substitutions. Generated 26 modified sequences.

#### II. AlphaFold & PredictSNP Limitations

**Key finding**: AlphaFold does not reliably predict the impact of point mutations (SNPs) on protein stability. Switched to PredictSNP.

-----

### 4c. Genetic Switch (Dry Lab)

**Objective**: Toggle between biosurfactant expression and campesterol production to prevent cellular overload.

**Switch Design Concepts Explored**:

  - **Thermal toggle switch**: Promising: steroid synthesis generates heat naturally; pausing cooling lets temperature rise and triggers state switch.
  - **Metabolic load-based switch**: Endorsed by PI.
  - **Yeast-to-hyphal morphological transition**: Exploits *Yarrowia*'s dimorphic growth.

-----

### 4d. Molecular Dynamics Simulation Protocol

*(Detailed bash pipeline documented)*

-----

## 5\. Results

### 5.1 Wet Lab Results

#### PCR & Colony Confirmation

Successful amplification was achieved for various hydrophobin inserts, followed by systematic validation of transformants.

\<div align="center"\>
\<img src="Figures/Figure 1 Agarose gel of PCR amplified gBlocks.png" width="400" alt="gBlock PCR"\>
\<img src="Figures/Figure 14. Q5 PCR result 1= ladder, 2=HFBI, 3= HFBII, 4= MBSP1, 5=pBEVY, 6= MF.png" width="400" alt="Q5 PCR"\>
<br>
\<em\>\<b\>Left:\</b\> PCR of gBlocks. \<b\>Right:\</b\> Q5 high-fidelity PCR results.\</em\>
\</div\>

\<div align="center"\>
\<img src="Figures/Fig16\_18.png" width="850" alt="Combined Colony PCR"\>
<br>
\<em\>\<b\>Figures 16-18.\</b\> Representative colony PCR results verifying MBSP1, HFBI, and HFBII integration.\</em\>
\</div\>

#### pET29-linker-sfGFP Vector Construction & Sequencing

  - 21 bp linker successfully inserted upstream of sfGFP via Gibson assembly
  - Confirmed by Sanger sequencing (correct linker sequence and reading frame)

\<div align="center"\>
\<img src="Figures/Figure 6. Sequencing results for MBSP1, HFBI (natural sequence) and the HFBI.png" width="450" alt="Sequencing Results"\>
\<img src="Figures/Figure 8. Sequencing result for linker plasmid.png" width="450" alt="Linker Sequencing"\>
<br>
\<em\>\<b\>Sequencing Data:\</b\> High-quality chromatograms confirming the sfGFP-linker-target reading frame.\</em\>
\</div\>

#### Protein Expression — SDS-PAGE Observations

  - **HFBI mutant**: more intense band than natural HFBI → **Cys→Ser substitutions improved protein expression**
  - **MBSP1**: band observed below the expected \~50 kDa → suspected cleavage of sfGFP fusion during purification

\<div align="center"\>
\<img src="Figures/Figure 7. SDS-PAGE for MBSP1, HFBI (natural sequence) and HFBI (mutated sequence).png" width="400" alt="SDS-PAGE"\>
\<img src="Figures/Figure 9. GFP expression in E. coli.png" width="450" alt="GFP Tube"\>
<br>
\<em\>\<b\>Protein Analysis:\</b\> SDS-PAGE showing higher yield for mutant HFBI (left) and visible GFP fluorescence in pellet (right).\</em\>
\</div\>

#### Live-cell Time-lapse Microscopy

  - GFP fluorescence signal monitored over 42 time points per position (10 min intervals).

#### *Y. lipolytica* Growth Modelling

  - Growth curves successfully obtained for both glucose and oil media.

### 5.2 Dry Lab Results

#### DHCR7 Enzyme Screening

  - Molecular docking completed for all 10 DHCR7 variants.
  - Best-performing complexes selected for 20 ns MD simulations.

#### Hydrophobin pI Analysis

  - 26 Lys/Arg→Asp/Glu substitution variants generated; pI reduced to 4.05–4.22.

-----

## 6\. BioBrick Parts Contribution

We submitted standardized parts to the iGEM Registry to facilitate future surfactant research.

\<div align="center"\>
\<img src="Figures/BBa\_K4661015.png" width="800" alt="BioBrick BBa\_K4661015"\>
<br>
\<em\>\<b\>Part BBa\_K4661015:\</b\> HFBI (mutant)-Linker-sfGFP cassette.\</em\>
\</div\>

\<div align="center"\>
\<img src="Figures/스크린샷 2026-03-30 173808.png" width="600" alt="Primer Sequence"\>
<br>
\<em\>Validation primer sequences for Registry submission.\</em\>
\</div\>

-----

## 7\. Conclusions & Future Directions

### What Was Achieved

\<div align="center"\>
\<img src="Figures/Figure 5. Summary of wet lab activities performed in E. coli.png" width="800" alt="Wet Lab Summary"\>
<br>
\<em\>\<b\>Figure 5.\</b\> Schematic summary of experimental pipeline in E. coli.\</em\>
\</div\>

| Area | Key Outcome |
|------|------------|
| **Wet Lab** | Successful expression of MBSP1 and HFBI (natural and mutant) in *E. coli*; Cys→Ser mutations shown to increase yield |
| **Dry Lab** | Molecular docking and MD simulations completed for 10 DHCR7 variants; AlphaFold limitations quantitatively characterised; pI-reduced hydrophobin variants designed |
| **Modelling** | *Y. lipolytica* growth model established for glucose and oil media |

### Future Work

We proposed a transition to a "Marionette" promoter system for tighter regulation.

\<div align="center"\>
\<img src="Figures/Figure 10. Our idea for improving our promotor and ensuring inducible expression of our target protein.png" width="700" alt="Promoter Optimization"\>
<br>
\<em\>\<b\>Figure 10.\</b\> Proposed optimization of leaky vs. tight inducible promoters.\</em\>
\</div\>

1.  Quantify thermodynamic stability of hydrophobin variants using **FoldX / PyFoldX**
2.  Re-evaluate SNP impact using **AlphaMissense**
3.  Transfer and validate hydrophobin expression and secretion in *S. cerevisiae* and *Y. lipolytica*
4.  Test campesterol production using WCO as the sole carbon source
5.  Implement genetic switch (thermal toggle or dimorphic transition)
6.  Apply ERG-5 → DHCR7 metabolic engineering in *Y. lipolytica*

### Assumptions & Limitations

  - AlphaFold structures lack experimental validation.
  - MD simulation length (20 ns) may be insufficient to capture large-scale conformational changes.

-----

## 8\. References

1.  Du, H.X. et al. Engineering *Yarrowia lipolytica* for campesterol overproduction. *PLoS ONE* **11** (2016)
2.  Zhang, Y. et al. Improved campesterol production in engineered *Yarrowia lipolytica* strains. *Biotechnol. Lett.* **39** (2017)
3.  Jumper, J. et al. Highly accurate protein structure prediction with AlphaFold. *Nature* **596** (2021)
4.  Mirdita, M. et al. ColabFold: making protein folding accessible to all. *Nat. Methods* **19** (2022)
5.  Trott, O. & Olson, A.J. AutoDock Vina: Improving the speed and accuracy of docking with a new scoring function, efficient optimization, and multithreading. *J. Comput. Chem.* (2009)
6.  Pettersen, E.F. et al. UCSF Chimera — A visualization system for exploratory research and analysis. *J. Comput. Chem.* **25** (2004)
7.  Laskowski, R.A. & Swindells, M.B. LigPlot+: Multiple ligand-protein interaction diagrams for drug discovery. *J. Chem. Inf. Model.* **51** (2011)
8.  Stierand, K., Maaß, P.C. & Rarey, M. Molecular complexes at a glance: Automated generation of two-dimensional complex diagrams. *Bioinformatics* **22** (2006)
9.  Cock, P.J.A. et al. Biopython: Freely available Python tools for computational molecular biology and bioinformatics. *Bioinformatics* **25** (2009)
10. Bendl, J. et al. PredictSNP: Robust and Accurate Consensus Classifier for Prediction of Disease-Related Mutations. *PLoS Comput. Biol.* **10** (2014)
11. Schymkowitz, J. et al. The FoldX web server: An online force field. *Nucleic Acids Res.* **33** (2005)
12. Radusky, L.G. & Serrano, L. PyFoldX: enabling biomolecular analysis and engineering along structural ensembles. *Bioinformatics* **38** (2022)
13. Jun Cheng et al. Accurate proteome-wide missense variant effect prediction with AlphaMissense. *Science* **381**, eadg7492 (2023)
14. Leon, M. et al. A computational method for the investigation of multistable systems and its application to genetic switches. *BMC Syst. Biol.* **10** (2016)
15. Gardner, T.S., Cantor, C.R. & Collins, J.J. Construction of a genetic toggle switch in *Escherichia coli*. *Nature* **403** (2000)
16. Bonnet, J., Subsoontorn, P. & Endy, D. Rewritable digital data storage in live cells via engineered control of recombination directionality. *Proc. Natl Acad. Sci. USA* **109** (2012)

-----

## 9\. 👥 Team & Author

\<div align="center"\>
\<img src="Figures/YarroWCO.png" width="800" alt="iGEM KU Leuven 2023 Team"\>
<br>
\<em\>\<b\>iGEM KU Leuven 2023 Team 'YarroWCO' at Arenberg Castle.\</b\>\</em\>
\</div\>

<br>

\<div align="center"\>
[🌐 Official Wiki](https://2023.igem.wiki/kuleuven/) | [🔬 Project Description](https://2023.igem.wiki/kuleuven/description) | [📊 Model](https://2023.igem.wiki/kuleuven/model)
\</div\>

```
```
