# 🍺 YarroWCO: Sustainable Steroid Precursor Production (iGEM 2023)

![Competition](https://img.shields.io/badge/Competition-iGEM%202023-blue)
![Award](https://img.shields.io/badge/Award-Silver%20Medal-silver)
![Role](https://img.shields.io/badge/Role-Wet%20%26%20Dry%20Lab%20Core-green)
![Tech](https://img.shields.io/badge/Tools-AlphaFold%20%7C%20Amber%20%7C%20AutoDock-orange)

> **Project Goal:** Engineering *Yarrowia lipolytica* to upcycle Waste Cooking Oil (WCO) into **Campesterol**, a high-value precursor for pharmaceutical steroids.

🔗 **[View Official iGEM Wiki](https://2023.igem.wiki/kuleuven/)**

## 📌 Project Overview
**Waste Cooking Oil (WCO)** poses a significant environmental burden, often clogging sewage systems ("fatbergs") or contaminating water sources. Our team, representing **KU Leuven**, proposed a circular economy solution: using synthetic biology to turn this pollutant into a valuable resource.

We engineered the oleaginous yeast ***Yarrowia lipolytica*** to:
1.  **Consume WCO efficiently** by expressing biosurfactants to emulsify the oil.
2.  **Redirect metabolic flux** from lipid storage to the production of **Campesterol** (a steroid drug precursor).

## 🔬 My Role: Bridging Wet & Dry Lab
**Timeline:** Jan 2023 – Nov 2023  
**Position:** Core Team Member (Integrated Wet & Dry Lab)

I operated at the intersection of computational modeling and experimental validation. My primary focus was **In Silico Protein Engineering** to identify optimal enzyme candidates, followed by **Wet Lab engineering** of biosurfactant systems.

---

## 💻 In Silico Engineering (Dry Lab)
The Campesterol biosynthesis pathway requires the reduction of ergosta-5,7-dienol. To achieve this, we needed a highly efficient **7-Dehydrocholesterol Reductase (DHCR7)**.

### 1. Structure Prediction (AlphaFold)
Since crystal structures were unavailable for many candidate enzymes across different species, I utilized **AlphaFold Colab** to predict 3D structures with high confidence.
* **Objective:** Generate PDB models for DHCR7 variants.
* **Outcome:** Validated active site geometry before docking.

### 2. Molecular Docking (AutoDock Vina)
I screened multiple DHCR7 candidates to evaluate their binding affinity to the substrate (ergosta-5,7-dienol).
* **Tools:** UCSF Chimera, AutoDock Vina.
* **Process:** Prepared ligand/receptor files, defined search space around the active site, and ranked candidates based on binding energy (kcal/mol).

### 3. Molecular Dynamics (Amber)
To ensure the enzymes remained stable under physiological conditions, I performed MD simulations using supercomputing resources.
* **Tools:** Amber (Sander/PMEMD).
* **Analysis:** Calculated RMSD (Root Mean Square Deviation) and RMSF (Fluctuation) to assess structural stability and flexibility in a solvated environment.

---

## 🧬 Experimental Validation (Wet Lab)
To enable the yeast to consume oil, we needed to increase the bioavailability of WCO. I focused on the "Biosurfactant Module."

* **Strain Engineering:** Engineered *E. coli* to express **Hydrophobins** (Biosurfactants) to test the concept of oil emulsification.
* **Cloning Workflow:**
    * Performed **Gibson Assembly** to construct expression vectors.
    * Conducted **colony PCR (cPCR)** for screening.
    * Optimized **IPTG-induced** gene expression.
* **Reporter System:** Co-expressed Green Fluorescent Protein (GFP) to visually track biosurfactant production and aggregation at the oil-water interface.

---

## 🛠 Tech Stack & Tools
| Category | Tools Used |
| :--- | :--- |
| **Structure Prediction** | AlphaFold Colab, Homology Modeling |
| **Simulation & Docking** | Amber (MD), AutoDock Vina, UCSF Chimera |
| **Data Analysis** | Python (Pandas, NumPy), R (Growth modeling) |
| **Wet Lab Techniques** | Gibson Assembly, PCR, Fluorescence Microscopy, Bacterial Culture |

## 🏆 Achievements
* **Silver Medal:** Awarded at the **iGEM Grand Jamboree 2023** (Paris).
* **Best Education Nomination:** Recognized for excellence in scientific communication and public engagement.

## 📬 Contact
**Jeong-Ho (Jay) Choi**
* **LinkedIn:** [Your LinkedIn Profile Link]
* **Email:** [Your Email Address]

---
*For a detailed walkthrough of the project, experimental data, and team members, please visit our [Wiki Description Page](https://2023.igem.wiki/kuleuven/description).*
