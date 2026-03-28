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
6. [Conclusions & Future Directions](#6-conclusions--future-directions)
7. [References](#7-references)

---

## 1. Project Introduction

### Background: Why This Project?

Over **two billion tons of waste cooking oil (WCO)** were produced globally in 2016 alone. Belgium is renowned for its fried food culture; in 2021, approximately 88,000 metric tons of WCO were generated in the country. Just one liter of WCO can contaminate over one million liters of water.

The EU currently converts WCO into biodiesel (UCOME), but combustion still releases CO₂. This project explores a higher-value alternative.

### Core Concept

```
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
```

- **Steroid drug market**: >1 million tons produced annually; market value ~$10 billion USD
- **Campesterol**: critical precursor for corticosteroids, sex hormones, and other steroids
- **Core challenge**: campesterol currently relies on plant/animal extraction → replace with WCO-based biosynthesis via *Y. lipolytica*

### Project Structure

| Component | Scope | Team |
|-----------|-------|------|
| **Wet Lab** | Expression vector construction for biosurfactants (hydrophobins); validation in *E. coli*; *Y. lipolytica* growth modelling | Wet lab team |
| **Dry Lab** | DHCR7 enzyme screening; hydrophobin design; genetic switch; growth model construction | Dry lab team |

---

## 2. Overview & Key Models

> 📌 **iGEM 2023 Best Model Nominee**  
> Official model page: [https://2023.igem.wiki/kuleuven/model](https://2023.igem.wiki/kuleuven/model)

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

---

## 3. Experimental Design

### 3a. Engineering Cycle (DBTL)

**Three complete DBTL iterations** were performed in *E. coli*:

```
Design ──► Build ──► Test ──► Learn
  ▲                              │
  └──────────────────────────────┘
```

#### Iteration 1: First Cloning Attempt in pET28

**Design**
- pET28 backbone + AcGFP-linker-hydrophobin fusion constructs
- Screened biosurfactants: HFBI, HFBII, HGFI, MBSP1, and cysteine-mutant variants (8 constructs total)
- Golden Gate cloning strategy

**Build**
- pET28 backbone amplified with Q5 High-Fidelity 2× Master Mix (NEB); 50 µL reaction, 10 ng plasmid template
- gBlock inserts amplified with Taq DNA Polymerase (NEB); 5 ng gBlock DNA

**Test**
- AcGFP and HGFI_full_mutated PCR successful; pET28 backbone PCR failed

**Learn**
- Backbone amplification failure investigated → transition to a new cloning strategy

#### Iterations 2 & 3: Transition to pET29-linker-sfGFP System

**Design**
- pET29-sfGFP backbone + 21 bp linker (SGGSGGS) + hydrophobin fusion
- Switched from Golden Gate (BsaI-based) to Gibson Assembly
- Final targets: MBSP1, HFBI (natural/mutant), HFBII (mutant), HGFI series

**Key Build Conditions**

```
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

---

### 3b. Experimental Protocols

#### Plasmid Extraction

```
Strains: E. coli DH10-beta carrying pET28, pET29, or pBEVY plasmids
Medium: LB broth + antibiotic (ampicillin 100 µg/mL or kanamycin 50 µg/mL)
Culture: 37°C, overnight (<18 h)
Centrifugation: 4,000 × g, 10 min
Kit: GeneJET Plasmid Miniprep Kit (ThermoFisher Scientific)
```

#### PCR Cycling Conditions

**Q5 Polymerase (backbone amplification)**

| Step | Temperature | Time |
|------|-------------|------|
| Initial denaturation | 98°C | 30 sec |
| Denaturation (×30) | 98°C | 10 sec |
| Annealing (×30) | NEB Tm Calculator value | 30 sec |
| Extension (×30) | 72°C | 3 min 30 sec |
| Final extension | 72°C | 2 min |

**Taq Polymerase (insert amplification)**

| Step | Temperature | Time |
|------|-------------|------|
| Initial denaturation | 95°C | 30 sec |
| Denaturation (×30) | 95°C | 30 sec |
| Annealing (×30) | NEB Tm Calculator value | 60 sec |
| Extension (×30) | 68°C | 20 sec |
| Final extension | 68°C | 5 min |

#### Protein Expression

```
Strain: E. coli BL21
Pre-culture: LB broth + kanamycin 50 µg/mL, 3 mL, overnight
Main culture: LB broth, 50 mL; IPTG induction at OD = 0.5 (final concentration: 400 µM)
Expression: 37°C, 3 h in the presence of IPTG
Harvest: 4,000 × g, 20 min
```

#### Protein Purification

```
Resuspension: 1× PBS
Sonication: 15 × 30 sec pulses (30 sec intervals)
Centrifugation: 16,000 × g, 20 min (collect supernatant)
Purification: HisPur Ni-NTA Resin (ThermoFisher Scientific)
              Manufacturer protocol followed, with 1 h additional shaking in resin
```

#### *Yarrowia lipolytica* Growth Curve

```
Inoculation: single colony → YPD 3 mL, overnight, 30°C, 200 rpm
Starting OD: diluted to 0.1
Carbon source conditions:
  - Oil medium:     1.85 mL oil + 48.15 mL YP    (3.7% v/v)
  - Glucose medium: 6.25 mL 40% glucose + 43.75 mL YP (5% w/v)
  (Carbon-equivalent concentrations based on molar carbon content)
Measurement: OD every 2 h over 60 h total
Replicates: 2 per condition
```

---

## 4. Lab Notebooks

### 4a. DHCR7 Enzyme Screening (Dry Lab)

**Period**: 1 July 2023 – 9 September 2023

#### I. Preparation (1/7 – 20/7)

**Motivation**  
The final step of the campesterol biosynthesis pathway requires delta-7-sterol reductase (DHCR7), which is not natively present in *Y. lipolytica*. Based on literature (Du et al. 2016; Zhang et al. 2017), 10 DHCR7 candidates from different organisms were selected for screening.

- Literature-sourced organisms: *Rattus norvegicus*, *Xenopus laevis*, *Homo sapiens*, *Gallus gallus*, *Danio rerio*, *Arabidopsis thaliana*, *Waddlia chondrophila*
- Additional *Danio rerio* homologs: *Mus musculus*, *Xenopus tropicalis*, *Bos taurus*

**Excluded organisms**:
- *Oryza sativa* (Os02g0465400): substantial structural divergence from other DHCR7 enzymes; no reviewed UniProt record
- *P. troglodytes*, *C. lupus*, *M. oryzae*: records removed or in unreviewed status

**Reference structure**: 4QUV (delta(14)-sterol reductase) — same protein family as DHCR7, high structural similarity → used to locate the NADPH binding site in DHCR7

#### II. Structure Prediction (28/7 – 2/8)

DHCR7 structures for *Gallus gallus* and *Waddlia chondrophila* were not deposited in the PDB and were therefore predicted using AlphaFold:

**Tools**: AlphaFold Colab & ColabFold (Google Colab, default settings)

**Gallus gallus — Prediction Quality**:

| Metric | Result |
|--------|--------|
| pLDDT (overall) | >80 for the majority of residues |
| pLDDT (N-terminus) | Low (expected for disordered region) |
| Caution region | Residues ~380 (pLDDT drop, coincides with lower MSA coverage) |
| PAE (high regions) | N-terminus and residues ~380 (PAE 20–30) |

**Waddlia chondrophila — Prediction Quality**:

| Metric | Result |
|--------|--------|
| pLDDT (overall) | >80 for most residues |
| Caution region | Residues 350–370 (pLDDT <70) |
| PAE (high regions) | N-terminus and residues 350–370 |

**Final selection**: AlphaFold Colab outputs chosen over ColabFold (marginally higher pLDDT values)

> ⚠️ **Assumptions & Limitations**: All structures are computational predictions without experimental validation. Prediction confidence is low at the N-terminus and in regions of reduced MSA coverage. Downstream docking and MD results should be treated as provisional.

#### III. Molecular Docking (1/8 – 15/9)

**Tool**: AutoDock Vina (UCSF Chimera)  
**Protocol**: provided by Prof. Jeremy Harvey  
**Ligands**: NADPH, ergosta-5,7-dienol (downloaded from PubChem)

**Protocol validation**: Re-docking of NDP into 4QUV reproduced the crystallographic binding pose.

> **Bug note**: After DockPrep, a hydrogen atom was incorrectly labelled "HO"; AutoDock Vina interpreted this as Holmium (Ho). Resolved by renaming to "H".

**Docking runs**: 10 runs per ligand per enzyme (NADPH and ergosta-5,7-dienol)

**Double-check criteria** (suggested by Prof. Matheus Froeyen):

| Interaction Type | Assessment |
|-----------------|------------|
| No interactions at all | ❌ BAD |
| Hydrogen bonds present | ✅ GREAT |
| H-bond with UniProt annotated binding site residue | ⭐ AMAZING |
| Hydrophobic contacts only | ⚠️ OKAY |

**Visualisation tools**: UCSF Chimera (H-bond analysis), PoseView, LigPlot+

> **Technical issue**: Chimera surface calculation failed with mscalc error code 5 → PoseView and LigPlot+ used as alternatives for interaction analysis.

#### IV. Molecular Dynamics Simulations (19/9 – 9/9)

**Software**: AMBER22  
**Hardware**: NVIDIA RTX3080ti GPU  
**Input structures**: complexes selected from docking double-check with favourable interaction profiles

**MD Pipeline**:

```
1. Ligand preparation
   SDF (PubChem) → PDB conversion
   Unique atom naming (element + index, e.g. O01, H12)
   Residue name set to LIG
   antechamber (GAFF2 force field) → .prep file
   parmchk2 → .frcmod file (supplementary force field parameters)

2. Complex preparation
   Remove MODEL/ENDMDL lines
   Remove secondary structure (HELIX/SHEET) records
   Manually match docked ligand atom names to prepped ligand (verified atom-by-atom in Chimera)
   Truncate disordered C-terminal tail (~20 aa; low AlphaFold confidence, non-functional)
   LEaP → AMBER topology (.prmtop) + coordinate file (.inpcrd)

3. MD Simulation stages
   ① Energy minimisation        Run.min.cuda
   ② Heating: 0 → 300 K        Run.heat.cuda   (2 fs timestep)
   ③ Density equilibration      Run.density.cuda
   ④ Equilibration              Run.equil.cuda   2,500,000 steps × 2 fs = 5 ns
   ⑤ Production (5 stages)      Run.prod1–5.cuda 2,000,000 steps × 2 fs = 4 ns/stage = 20 ns total

4. Analysis
   RMSD:       cpptraj (Run.rms2)      — monitor after each production stage
   RMSF:       cpptraj (Run.tfactors2) — per-residue fluctuation
   H-bond dist: Run.hbond_dist         — track key distances (target: 2.7–3.5 Å)
   Visualisation: xmgrace / gracebat / Python / Excel
```

**Stability criteria**:

| Metric | Good sign | Warning sign |
|--------|-----------|--------------|
| RMSD | Plateaus over time | Continual increase |
| RMSF | No extreme spikes | Repeated high-amplitude fluctuations |
| H-bond distance | Maintained 2.7–3.5 Å | Exceeds 3.5 Å and does not recover |
| Ligand position | Remains in binding pocket | Exits binding pocket |

---

### 4b. Hydrophobin Design (Dry Lab)

**Period**: 1 August 2023 – 8 September 2023

#### Design Rationale

Hydrophobins exhibit optimal emulsification activity at alkaline pH (~9), but *Y. lipolytica* prefers acidic conditions, and fermentation pH drops rapidly without active control. **Goal: engineer an HFBI variant with a lower pI that retains emulsification activity at acidic pH.**

**Starting protein**: HFBI (PDB: 2FZ6, 75 aa, 2× Lys + 1× Arg)

#### I. Sequence Generation (22/8 – 24/8)

**Strategy** (proposed by PI Vitor Pinheiro):
- Use BioPython to calculate protein pI
- Enumerate all combinations of Lys/Arg → Glu/Asp substitutions

**Results**:
- 26 modified sequences generated
- pI range: 4.05–4.22 (default pH search interval); lowest pI: 3.17 (extended search interval)
- Additional variants: random 3× Leu→Asp; all 7× Leu→Asp substitutions

#### II. AlphaFold — Identified Limitation (24/8 – 31/8)

**Key finding**: AlphaFold does not reliably predict the impact of point mutations (SNPs) on protein stability.

| Comparison | Expected outcome | AlphaFold result |
|------------|-----------------|-----------------|
| HFBI vs HFBI (3× Leu→Asp) | Significant structural change | Near-identical structures |
| HFBI vs HFBI (7× Leu→Asp) | Destabilised or unstructured regions | Still highly similar structure |

→ AlphaFold deemed unsuitable for mutation-stability analysis → replaced with PredictSNP

#### III. PredictSNP Mutation Impact Prediction (4/9 – 8/9)

> ⚠️ **Assumption & Limitation**: PredictSNP was trained on human protein data. Hydrophobins are fungal proteins; prediction accuracy for this class is not guaranteed. Results should be interpreted with caution.

**Lowest-pI variant (K32D, R45D, K50D) — PredictSNP results**:

| Mutation | PredictSNP | MAPP | PhD-SNP | PolyPhen-1 | PolyPhen-2 | SIFT | SNAP |
|----------|-----------|------|---------|-----------|-----------|------|------|
| K32D | NEUTRAL | **DELETERIOUS** | NEUTRAL | NEUTRAL | NEUTRAL | NEUTRAL | NEUTRAL |
| R45D | NEUTRAL | **DELETERIOUS** | NEUTRAL | NEUTRAL | **DELETERIOUS** | NEUTRAL | **DELETERIOUS** |
| K50D | NEUTRAL | **DELETERIOUS** | NEUTRAL | NEUTRAL | NEUTRAL | NEUTRAL | NEUTRAL |

Majority-tool consensus: NEUTRAL → mutations unlikely to strongly destabilise the protein

**Leu→Asp substitution variants**: Unanimously predicted DELETERIOUS across all tools → structural stability expected to be compromised

#### Next Steps
- **FoldX / PyFoldX**: thermodynamic stability quantification via force-field calculations
- **AlphaMissense** (Google DeepMind, released September 2023): re-evaluate SNP impact predictions

---

### 4c. Genetic Switch (Dry Lab)

**Period**: 1 August 2023 – 14 September 2023

#### Objective

Toggle between biosurfactant expression and campesterol production to prevent cellular overload.

#### Expert Consultations

- **Alexander Fedorec** (UCL, Division of Biosciences)  
  Meetings: 30 August 2023 & 12 September 2023 (Rega Institute, Leuven)

#### Switch Design Concepts Explored

| Concept | Assessment |
|---------|------------|
| Concentration-based feedback loop | ❌ Biosurfactant (secreted) and campesterol (intracellular) both extremely difficult to detect in real time |
| RAD switch | Ruled out — insufficient time and expertise |
| **Thermal toggle switch** | ✅ Promising: steroid synthesis generates heat naturally; pausing cooling lets temperature rise and triggers state switch; energy-saving |
| Metabolic load-based switch | ✅ Endorsed by both Alex Fedorec and PI Vitor |
| Yeast-to-hyphal morphological transition | ✅ Exploits *Yarrowia*'s dimorphic growth: yeast phase = surfactant production; hyphal phase = campesterol production |
| Quorum sensing | Feasibility in *Y. lipolytica* requires further investigation |

**Reference**: Gardner, T.S., Cantor, C.R. & Collins, J.J. (2000) genetic toggle switch in *E. coli* (*Nature* 403)

---

### 4d. Molecular Dynamics Simulation Protocol

> Written: 24 September 2023 | Author: Julia Bandera | Supervisor: Prof. Mathy Froeyen

**Remote access**: DWService (agent: geuze) → GPU workstation at home/igem (terminal only, no GUI)

#### Full Pipeline — Script Execution Order

```bash
# ── 1. LIGAND PREPARATION (run once per ligand) ──────────────────────────────
./Run.sdf2pdb [ligand_filename]
./Run.restore_pdb [ligand_filename.pdb] [ligand_filename.out.pdb]
./Run.antechamber2 [ligand_filename] 0     # GAFF2 force field; net charge = 0
./Run.parmchk2     [ligand_filename] 0     # supplementary FF parameters

# ── 2. COMPLEX PREPARATION ───────────────────────────────────────────────────
cp [complex.pdb] [complex.out.pdb]
# Manually remove MODEL/ENDMDL and HELIX/SHEET records in a text editor
# Match docked ligand atom names to prepped ligand names (verify in Chimera)
# Truncate low-confidence C-terminal tail in text editor
sed -i -- 's/UNK/LIG/g' [complex.out.pdb]   # standardise residue name
./Run.leap.sol                                # generate topology + coordinate files

# ── 3. MD SIMULATION ─────────────────────────────────────────────────────────
./Run.min.cuda           # energy minimisation
./Run.heat.cuda          # heating 0 → 300 K, 2 fs timestep
./Run.density.cuda       # solvent density adjustment
./Run.equil.cuda         # equilibration: 2,500,000 steps × 2 fs = 5 ns
./Run.makepdb equil      # convert equil.rst → equil.pdb for visual inspection

./Run.prod1.cuda         # production stage 1:  4 ns
./Run.prod2.cuda         # production stage 2:  4 ns
./Run.prod3.cuda         # production stage 3:  4 ns
./Run.prod4.cuda         # production stage 4:  4 ns
./Run.prod5.cuda         # production stage 5:  4 ns  →  total: 20 ns

# ── 4. ANALYSIS ──────────────────────────────────────────────────────────────
./Run.rms2               # RMSD over trajectory (adjust residue mask)
./Run.tfactors2          # RMSF per backbone atom (adjust residue mask)
./Run.hbond_dist         # H-bond distance tracking (adjust atom pairs)

# Plotting (use gracebat when no GUI is available)
gracebat [input.agr]     -hdevice PNG -autoscale xy -printfile [output.png]
gracebat [input.bfactor] -hdevice PNG -autoscale xy -printfile [output.png]
gracebat [input.dat]     -hdevice PNG -autoscale xy -printfile [output.png]
```

> ⚠️ **Critical**: Production stages must run sequentially — do not start the next stage before the previous one has finished.

**H-bond distance interpretation**:
- Typical cutoff (heavy atoms): **3.5 Å**
- Stable H-bond: distance remains within **2.7–3.5 Å** throughout simulation
- Bond rupture: distance exceeds 3.5 Å and does not return → ligand may form new contacts with neighbouring residues

---

## 5. Results

### 5.1 Wet Lab Results

#### pET29-linker-sfGFP Vector Construction
- 21 bp linker successfully inserted upstream of sfGFP via Gibson assembly
- Confirmed by Sanger sequencing (correct linker sequence and reading frame)

#### Biosurfactant Cloning Summary

| Construct | Insert size | PCR | Colony PCR | Sequencing | Expression |
|-----------|------------|-----|-----------|-----------|-----------|
| MBSP1 | 897 bp | ✅ | ✅ | ✅ | ✅ |
| HFBI (natural) | 231 bp | ✅ | ✅ | ✅ | ✅ |
| HFBI (mutant) | 231 bp | ✅ | ✅ | ✅ | ✅ (higher yield) |
| HFBII (mutant) | 294 bp | ✅ | ✅ | ❌ (insert not confirmed) | — |
| HFBII (natural) | 294 bp | ✅ | ❌ | — | — |
| HGFI series | 324 bp | ✅ | ❌ | — | — |

#### Protein Expression — SDS-PAGE Observations

- **HFBI mutant**: more intense band than natural HFBI → **Cys→Ser substitutions improved protein expression**
- **MBSP1**: band observed below the expected ~50 kDa → suspected cleavage of sfGFP fusion during purification
- **HFBI natural/mutant**: faint bands at differing heights → possible incomplete cleavage of sfGFP from hydrophobin

#### Live-cell Time-lapse Microscopy
- GFP fluorescence signal monitored over 42 time points per position (10 min intervals for first hour; 25 min intervals thereafter)
- Platform: Nikon Ti-Eclipse inverted microscope; cells plated on AB-agarose pads containing IPTG
- Controls: uninduced BL21 (no IPTG) and untransformed BL21 (no kanamycin, no IPTG)
- Data analysed with NIS-Elements Viewer (Nikon) and Fiji (ImageJ)

#### *Y. lipolytica* Growth Modelling
- Growth curves successfully obtained for both glucose and oil media
- Lag, exponential, and stationary phases all captured
- Foundation established for future WCO-based campesterol production experiments

### 5.2 Dry Lab Results

#### DHCR7 Enzyme Screening
- Molecular docking completed for all 10 DHCR7 variants with NADPH and ergosta-5,7-dienol
- Binding interactions analysed via docking score, hydrogen bond count, and interaction diagrams (PoseView / LigPlot+)
- Best-performing complexes selected for 20 ns MD simulations
- RMSD, RMSF, and H-bond distance trajectories analysed to assess binding stability

#### Hydrophobin pI Analysis
- 26 Lys/Arg→Asp/Glu substitution variants generated; pI reduced to 4.05–4.22
- PredictSNP consensus: Lys/Arg substitutions predominantly NEUTRAL → protein stability likely preserved
- Leu→Asp substitutions: unanimously DELETERIOUS across all prediction tools → not recommended

#### Genetic Switch Design
- Three viable switch concepts identified: thermal toggle, metabolic load sensor, dimorphic transition
- Conceptual design completed; full implementation not achieved within project timeline

---

## 6. Conclusions & Future Directions

### What Was Achieved

| Area | Key Outcome |
|------|------------|
| **Wet Lab** | Successful expression of MBSP1 and HFBI (natural and mutant) in *E. coli*; Cys→Ser mutations shown to increase yield |
| **Dry Lab** | Molecular docking and MD simulations completed for 10 DHCR7 variants; AlphaFold limitations quantitatively characterised; pI-reduced hydrophobin variants designed |
| **Modelling** | *Y. lipolytica* growth model established for glucose and oil media |

### Future Work

1. Quantify thermodynamic stability of hydrophobin variants using **FoldX / PyFoldX**
2. Re-evaluate SNP impact using **AlphaMissense**
3. Transfer and validate hydrophobin expression and secretion in *S. cerevisiae* and *Y. lipolytica*
4. Test campesterol production using WCO as the sole carbon source
5. Implement genetic switch (thermal toggle or dimorphic transition)
6. Apply ERG-5 → DHCR7 metabolic engineering in *Y. lipolytica*

### Assumptions & Limitations

| Item | Limitation |
|------|-----------|
| AlphaFold structures | No experimental validation; docking and MD results are provisional |
| PredictSNP | Trained on human data; accuracy for fungal proteins is not guaranteed |
| MD simulation length | 20 ns may be insufficient to capture large-scale conformational changes |
| Growth media | Carbon-molar equivalence applied, but other nutritional differences exist between glucose and oil media |
| DHCR7 transmembrane topology | Membrane environment not included in docking/MD; binding pocket geometry may differ in native membrane context |

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

<div align="center">

**iGEM KU Leuven 2023 | YarroWCO**

[🌐 Official Wiki](https://2023.igem.wiki/kuleuven/) | [🔬 Project Description](https://2023.igem.wiki/kuleuven/description) | [📊 Model](https://2023.igem.wiki/kuleuven/model) | [📋 Results](https://2023.igem.wiki/kuleuven/results) | [🛠 Engineering](https://2023.igem.wiki/kuleuven/engineering)

</div>
