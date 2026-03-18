# 🧬 NetworkSuite — Scientific Network Analysis Platform

[![Live Demo](https://img.shields.io/badge/🌐%20Live%20Demo-Visit%20Tool-2563EB?style=for-the-badge)](https://sequensolutions.com/tools/networksuite/)
[![Version](https://img.shields.io/badge/Version-5.0-7C3AED?style=for-the-badge)](https://github.com/Abhishek-MSBI/NetworkSuite)
[![License](https://img.shields.io/badge/License-MIT-059669?style=for-the-badge)](LICENSE)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES2022-F59E0B?style=for-the-badge&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Made By](https://img.shields.io/badge/Made%20by-Sequensolutions-EC4899?style=for-the-badge)](https://sequensolutions.com/tools/networksuite/)

> **A fully client-side, publication-grade protein interaction network analysis platform built for computational biologists, cancer genomics researchers, and bioinformaticians. Zero installation. Zero server. Open in your browser and start analysing.**

---

## 🔗 Live Tool

**▶️ [https://abhishek-msbi.github.io/NetworkSuite/](https://sequensolutions.com/tools/networksuite/)**

No installation required. Works entirely in the browser.

---

## 🖥️ Screenshot

> *Publication-grade network canvas with interactive analysis sidebar and results panels.*

---

## ✨ Feature Overview

| Module | Description |
|---|---|
| 🔗 **STRING DB Integration** | Query STRING protein interaction database directly — single gene seed expansion or multi-gene network |
| 📂 **CSV Upload** | Drag-and-drop edge list import (auto-detects Source/Target/Score columns) |
| 🧠 **Hub Detection** | 5 centrality methods: Degree, Betweenness, Closeness, MNC, MCC (Bron–Kerbosch clique-based) |
| 🗺️ **Pathway Enrichment** | Enrichr API — GO BP/MF/CC, KEGG, WikiPathways, Reactome, MSigDB Hallmark |
| 💊 **Drug-Target Scan** | ChEMBL API integration to identify druggable candidates from hub genes |
| 🏘️ **Community Detection** | Label Propagation algorithm with visual cluster coloring |
| 🔬 **Cellular View** | GO Cellular Component layout via MyGene.info — visualise Nucleus/Membrane/Cytoplasm/Mitochondria |
| 📍 **Shortest Path** | Dijkstra's algorithm between any two genes with visual path highlighting |
| 🤝 **Jaccard Similarity** | Common neighbor analysis between gene pairs with Jaccard coefficient |
| 💥 **In-Silico Knockout** | Remove a gene node and analyse network fragmentation; fully reversible |
| 📊 **Publication Charts** | Plotly.js bar charts for all enrichment sources — exportable at 600 DPI |
| 📤 **Export Suite** | PNG (600 DPI), TIFF (600 DPI), SVG (vector), CSV edge list, JSON full analysis, PDF report |
| 🔗 **Shareable Links** | LZ-String compressed URL encoding for sharing networks |
| 🎨 **Style Controls** | Customisable node color/size by degree or numeric attributes, custom color gradients |

---

## 🚀 Quick Start

### Option 1 — Use Live (Recommended)
Open **[https://abhishek-msbi.github.io/NetworkSuite/](https://sequensolutions.com/tools/networksuite/)** in any modern browser.

### Option 2 — Run Locally
```bash
git clone https://github.com/Abhishek-MSBI/NetworkSuite.git
cd NetworkSuite
# Open index.html in your browser
open index.html   # macOS
start index.html  # Windows
```

No build step, no npm install, no dependencies to manage. All libraries loaded via CDN.

---

## 📖 Usage Guide

### 1. Load a Network

**From STRING DB:**
- Enter gene symbols (e.g. `TP53`, `BRCA1`, `PTEN`) in the STRING Query panel
- Set species (`9606` = Human), minimum interaction score (default `700`), and additional interactors
- Click **Fetch STRING Network** — data is fetched live from the STRING API

**From CSV file:**
- Prepare a CSV with columns: `source, target` (and optionally `score`)
- Drag and drop onto the upload zone or click to browse
- The tool auto-detects column names matching common naming conventions

**Example CSV format:**
```csv
source,target,score
TP53,MDM2,0.995
BRCA1,RAD51,0.871
EGFR,KRAS,0.712
```

### 2. Run Analysis

Use the **Control Panel** sidebar tabs:
- **Network** — layout options (fCoSE, Cose, Grid, Circle, Breadthfirst), view modes
- **Analysis** — Hub detection, Pathway enrichment, Drug scan, Community detection
- **Tools** — Shortest path, Jaccard similarity, In-silico knockout
- **Style** — Node color/size attribute mapping, color gradient control

Or click **⚡ Run All** in the header to execute the full pipeline automatically:
1. Hub detection (all 5 methods)
2. All 7 pathway enrichment libraries in parallel
3. Community detection
4. Drug-target scan

### 3. Export Results

| Format | Description | Use Case |
|---|---|---|
| PNG 600 DPI | High-resolution raster | Journal figures |
| TIFF 600 DPI | Publication TIFF | Manuscript submission |
| SVG | Vector, infinitely scalable | Presentations |
| CSV | Edge list | Downstream tools |
| JSON | Full analysis dump | Data archival, reproducibility |
| PDF | Formatted analysis report | Collaborators, PIs |

---

## 🧬 Analysis Modules — In Depth

### Hub Gene Detection

Five centrality methods to identify key network nodes:

| Method | Description |
|---|---|
| **Degree** | Number of direct interactions |
| **Betweenness** | Fraction of shortest paths passing through the node |
| **Closeness** | Mean shortest path distance to all other nodes |
| **MNC** | Maximum Neighbourhood Component — max degree of neighbours |
| **MCC** | Maximum Clique Centrality — log-sum of clique memberships (Bron–Kerbosch) |

The top 30% of nodes (min 3, max 20) are highlighted as hubs.

### Pathway Enrichment (Enrichr API)

Gene lists are submitted to [Enrichr](https://maayanlab.cloud/Enrichr/) and queried against:
- **GO Biological Process 2023**
- **GO Molecular Function 2023**
- **GO Cellular Component 2023**
- **KEGG 2021 Human**
- **WikiPathways 2021 Human**
- **Reactome 2022**
- **MSigDB Hallmark 2020**

Results are sorted by p-value and visualised as horizontal bar charts (−log₁₀ p-value).

### Drug-Target Scanning (ChEMBL API)

Hub genes are queried against the [ChEMBL](https://www.ebi.ac.uk/chembl/) database:
- Matches gene symbols to ChEMBL target records
- Retrieves associated bioactive compounds (CHEMBL IDs)
- Prioritises top 10 hub genes as druggable candidates

### Community Detection (Label Propagation)

- 30-iteration Label Propagation algorithm with random tie-breaking
- Detects functional modules (communities of ≥ 2 nodes)
- Each cluster visualised with a distinct colour from a 10-colour palette
- Click any cluster card to highlight it on the canvas

### Cellular Compartment View

- Queries [MyGene.info](https://mygene.info/) for GO Cellular Component annotations
- Spatially arranges nodes by compartment: **Nucleus → Cytoplasm → Membrane → Extracellular → Mitochondria**
- Concentric ring layout reflecting biological cellular topology

---

## 🛠️ Technology Stack

| Library | Version | Purpose |
|---|---|---|
| [Cytoscape.js](https://js.cytoscape.org/) | 3.x | Network graph rendering & analysis |
| [cytoscape-fcose](https://github.com/iVis-at-Bilkent/cytoscape.js-fcose) | — | Force-directed compound graph layout |
| [Alpine.js](https://alpinejs.dev/) | 3.x | Reactive UI state management |
| [Plotly.js](https://plotly.com/javascript/) | — | Interactive enrichment bar charts |
| [PapaParse](https://www.papaparse.com/) | — | CSV parsing |
| [jsPDF](https://github.com/parallax/jsPDF) | — | PDF report generation |
| [LZ-String](https://github.com/pieroxy/lz-string) | — | URL compression for network sharing |
| [UTIF.js](https://github.com/photopea/UTIF.js) | — | TIFF image export |
| [Font Awesome](https://fontawesome.com/) | 6.x | Icons |
| [Inter](https://fonts.google.com/specimen/Inter) + [JetBrains Mono](https://www.jetbrains.com/lp/mono/) | — | Typography |

**External APIs used at runtime (no API key required):**
- [STRING DB](https://string-db.org/) — Protein interaction data
- [Enrichr (MaayanLab)](https://maayanlab.cloud/Enrichr/) — Pathway enrichment
- [ChEMBL (EBI)](https://www.ebi.ac.uk/chembl/) — Drug-target data
- [MyGene.info](https://mygene.info/) — GO cellular component annotations

---

## 📁 Repository Structure

```
NetworkSuite/
├── index.html          # Main application shell, layout, UI structure
├── app.js              # Application logic — Alpine.js data, all analysis engines
├── style.css           # Publication-grade clean light theme (CSS variables)
└── README.md           # This file
```

---

## 🧪 Example Workflows

### Cancer Hub Gene Workflow (TNBC)
```
1. Enter: TP53, BRCA1, EGFR, MYC, PIK3CA, PTEN, CDH1, RB1
2. Species: 9606 | Score: 700
3. Click "Fetch STRING Network"
4. Click ⚡ Run All
5. Review hub genes → enriched pathways → drug candidates
6. Export PDF report
```

### Seed Network Expansion
```
1. Enter single gene: RBM47
2. Score: 400 | Add Partners: 20
3. Click "Fetch STRING Network"
4. Run Betweenness hub detection
5. Check cellular compartment view
```

---

## 🌐 Deployment (GitHub Pages)

This repository is deployed via **GitHub Pages**.

To deploy your own fork:
1. Fork this repository
2. Go to **Settings → Pages**
3. Source: **Deploy from branch → main → / (root)**
4. Your live URL: `https://<your-username>.github.io/NetworkSuite/`

---

## 📜 Citation

If you use NetworkSuite in your research, please cite:

```
Abhishek S R (2026). NetworkSuite v5.0 — Scientific Network Analysis Platform.
Sequensolutions. https://github.com/Abhishek-MSBI/NetworkSuite
```

---

## 👤 Author

**Abhishek S R**  
Master's in Bioinformatics | Cancer Genomics Researcher  
Founder, [Sequensolutions](https://github.com/Abhishek-MSBI)  

[![GitHub](https://img.shields.io/badge/GitHub-Abhishek--MSBI-181717?style=flat&logo=github)](https://github.com/Abhishek-MSBI)

---

## 📄 License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---

*Built with ❤️ for the bioinformatics community. Part of the Sequensolutions tool suite.*
