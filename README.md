# HeliXplorer

### Interactive 3D DNA Visualization and Sequence Analysis

**HeliXplorer** is an interactive, browser-based DNA visualization and introductory bioinformatics workspace developed under **Systematic Biologic**. It combines a three-dimensional DNA double-helix model with sequence input, nucleotide-level inspection, composition analysis, open reading frame (ORF) detection, and a command-style terminal interface.

The application is designed for students, educators, and life-science enthusiasts who want to explore DNA structure and selected sequence properties in one visual environment.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Interface at a Glance](#interface-at-a-glance)
- [Getting Started](#getting-started)
- [Working with DNA Sequences](#working-with-dna-sequences)
- [Terminal Commands](#terminal-commands)
- [Recording and Exporting](#recording-and-exporting)
- [Technology Stack](#technology-stack)
- [Browser Requirements](#browser-requirements)
- [Scientific Scope and Limitations](#scientific-scope-and-limitations)
- [Project Structure](#project-structure)
- [Acknowledgements](#acknowledgements)
- [License](#license)

---

## Overview

DNA sequence data can be easier to explore when sequence-level information is connected to a visual representation of molecular structure. HeliXplorer brings together an interactive 3D helix, sequence navigation, base-pair inspection, and selected analytical summaries in a dark, workstation-inspired interface.

The application runs in a modern web browser. It does not require a dedicated backend server for its core visualization and sequence-analysis workflow. External libraries and NCBI retrieval require an internet connection.

## Key Features

### 1. Interactive 3D DNA Double Helix

- Render a three-dimensional DNA double-helix model.
- Rotate and inspect the molecular view interactively.
- Adjust automatic rotation speed.
- Change the visible sequence window and helical scale.
- Toggle display options, including the sugar-phosphate backbone, hydrogen-bond connections, ambient light particles, and nucleotide labels.
- Use the fullscreen control for an expanded visualization workspace.

### 2. DNA Sequence Input

- Paste a DNA sequence in FASTA format.
- Load a local FASTA file through the file input.
- Inspect the sequence record and visualize the loaded sequence.
- Clear the current input and load another sequence for exploration.

### 3. NCBI Nucleotide Record Retrieval

- Retrieve a nucleotide record using an NCBI nucleotide accession ID.
- Use the returned sequence as input for visualization and supported analyses.
- Internet access is required for remote retrieval. Availability and response behavior depend on NCBI and the network connection.

### 4. Sequence Navigation Track

- Navigate through the loaded sequence using the sequence track.
- View the currently displayed base-pair range.
- Select a nucleotide position to inspect its base-pair information in the nucleotide inspector.

### 5. Nucleotide Inspector and Base-Pair Information

- Inspect a selected nucleotide position.
- View the corresponding base-pair relationship.
- Review nucleotide identity and the displayed hydrogen-bond count for canonical Watson–Crick pairs.

### 6. Sequence Composition and GC Analysis

- View nucleotide composition summaries for A, T, G, and C.
- Review the overall GC percentage.
- Explore the GC-content plot calculated over a sliding window.

### 7. Open Reading Frame (ORF) Detection

- Identify candidate ORFs using canonical ATG start codons and stop-codon boundaries supported by the implementation.
- Review detected ORF positions and lengths in the interface.
- Treat results as candidate sequence features rather than proof of a functional gene.

### 8. Reverse Complement

- Generate the reverse-complement sequence for the loaded DNA.
- Copy the displayed reverse-complement result for use elsewhere.

### 9. Terminal Console

The terminal provides command-style access to selected sequence summaries and visualization controls. Type `help` in the console to display the supported commands.

Available commands include:

| Command | Description |
|---|---|
| `help` | Display the terminal command list. |
| `stats` | Show the record header, sequence length, and nucleotide counts. |
| `gc` | Show the overall GC percentage. |
| `orfs` | List detected candidate ORFs. |
| `revcomp` | Print the reverse-complement sequence. |
| `fasta` | Print the record header and a short sequence preview. |
| `length` | Display the sequence length. |
| `reset` | Reset the 3D camera and rendering options. |
| `clear` | Clear the terminal output. |
| `speed 1.5` | Set automatic rotation speed to the supplied numeric value. |
| `backbone` | Toggle the sugar-phosphate backbone display. |

The example `speed 1.5` sets the rotation speed to `1.5x`. Enter `help` in the running application for the current in-app command list.

### 10. Export and Viewport Recording

- Export a text-based analysis report using the **Export (.txt)** control.
- Record the live 3D DNA viewport using the **Record** control.
- Download the recorded viewport as a WebM video when supported by the browser.
- Switch the visualization into and out of fullscreen mode.

Recording captures the 3D viewport canvas, not the entire browser window or all interface panels.

### 11. Molecular Architecture Guide

The built-in molecular guide introduces key concepts represented in the visualization, including antiparallel DNA strands, Watson–Crick base pairing, and B-DNA helical geometry.

---

## Interface at a Glance

| Interface area | Purpose |
|---|---|
| **FASTA** | Paste or load a DNA sequence. |
| **NCBI Fetch** | Retrieve a nucleotide record by accession ID. |
| **3D viewport** | Explore the DNA double-helix representation. |
| **Display controls** | Adjust rotation, scale, and visible molecular features. |
| **Sequence Navigation Track** | Navigate the displayed sequence range and nucleotide positions. |
| **Dashboard** | Review GC content, candidate ORFs, and reverse-complement information. |
| **Terminal Console** | Run supported text commands and inspect summaries. |
| **Export / Record / Fullscreen** | Save a text report, record the 3D viewport, or expand the view. |

---

## Getting Started

### Option 1: Open the HTML file locally

1. Download or clone this repository.
2. Locate the main HTML file.
3. Open it in a recent version of Chrome, Microsoft Edge, Firefox, or another modern browser with support for the features you intend to use.
4. Connect to the internet so the page can load its externally hosted libraries and retrieve NCBI records.
5. Paste a DNA sequence in FASTA format or load a FASTA file.
6. Select **Visualize 3D Model** to load the sequence into the visualization.
7. Explore the 3D helix, sequence navigation track, dashboard, and terminal.

### Option 2: Run through a local web server

For a simple local server, open a terminal in the project directory and run:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

If the main HTML file is not named `index.html`, open its filename in the browser URL, for example `http://localhost:8000/your-file.html`.

---

## Working with DNA Sequences

A typical workflow is:

1. **Load a sequence:** paste FASTA-formatted DNA or choose a local FASTA file.
2. **Visualize:** select **Visualize 3D Model**.
3. **Explore structure:** rotate the model and adjust the display settings.
4. **Navigate:** use the Sequence Navigation Track to move through nucleotide positions.
5. **Inspect:** select a position to view nucleotide and base-pair details.
6. **Analyze:** review nucleotide composition, GC content, candidate ORFs, and reverse-complement information.
7. **Use the terminal:** enter `help` to see supported commands.
8. **Export or record:** save the text report or record the 3D viewport if needed.

For best results, use valid DNA sequence characters (`A`, `T`, `G`, and `C`) and a correctly formatted FASTA record. Ambiguous bases or non-DNA characters may not be represented or analyzed in the same way as canonical nucleotides.

---

## Recording and Exporting

### Text report

Use **Export (.txt)** to download the analysis report generated by the application.

### 3D viewport video

1. Load and visualize a DNA sequence.
2. Adjust the camera and display settings.
3. Select **Record** to begin capturing the 3D viewport.
4. Select the recording control again to stop and download the recording.

Video recording depends on browser support for the Canvas Capture Stream and MediaRecorder APIs. The output is WebM where supported. If recording is unavailable, try a recent version of Chrome or Edge.

### Fullscreen

Use the fullscreen control to enter or exit fullscreen mode. After changing fullscreen state, the page recalculates the visualization layout so that the Sequence Navigation Track can remain visible.

---

## Technology Stack

HeliXplorer is implemented as a client-side web application using:

- **HTML5** for page structure.
- **CSS and Tailwind CSS** for layout and styling.
- **JavaScript** for application state, sequence utilities, interaction, and visualization behavior.
- **Three.js** for the 3D molecular scene.
- **Three.js OrbitControls** for interactive camera navigation.
- **Chart.js** for the GC-content chart.
- **Lucide** for interface icons.
- **Google Fonts** for typography.

The application loads several dependencies from public CDNs. An internet connection is therefore recommended even when the HTML file is opened locally.

---

## Browser Requirements

A recent desktop browser is recommended for the complete experience.

- **Core visualization:** requires JavaScript and WebGL support.
- **External dependencies and NCBI retrieval:** require an internet connection.
- **Fullscreen:** requires browser support for the Fullscreen API.
- **Video recording:** requires support for `HTMLCanvasElement.captureStream()` and `MediaRecorder`; codec availability varies by browser.
- **Local serving:** a simple local HTTP server can be used if opening the file directly causes browser restrictions.

---

## Scientific Scope and Limitations

HeliXplorer is an educational visualization and introductory sequence-exploration tool. It is not a substitute for validated bioinformatics pipelines, molecular simulation software, or expert biological interpretation.

- The 3D helix is a visual representation and should not be interpreted as an experimentally determined structure for the loaded sequence.
- GC content and nucleotide counts describe sequence composition; they do not independently establish biological function.
- ORF detection identifies candidate reading frames according to the implemented rules. It does not establish gene expression, protein production, or biological activity.
- NCBI retrieval depends on external service availability and network connectivity.
- Results should be independently validated before being used in research, clinical, diagnostic, or other high-stakes settings.

---

## Project Structure

The application is currently distributed as a standalone HTML page. The HTML file contains the interface, styling references, and client-side JavaScript logic. External visualization, charting, icon, font, and styling libraries are loaded from CDNs.

```text
HeliXplorer/
└── index.html   # Main application page (filename may vary by repository)
```

If you publish the file under another name, update the example filename in this README to match your repository.

---

## Acknowledgements

HeliXplorer builds on open-source web technologies and libraries, including Three.js, Chart.js, Tailwind CSS, and Lucide. NCBI is used as the external source for nucleotide-record retrieval.

- Three.js: https://threejs.org/
- Chart.js: https://www.chartjs.org/
- Tailwind CSS: https://tailwindcss.com/
- Lucide: https://lucide.dev/
- NCBI Nucleotide: https://www.ncbi.nlm.nih.gov/nuccore/

Please consult the respective projects' documentation and license terms when redistributing or modifying their software.

---

## License

No license is specified in this README. Add a `LICENSE` file before presenting the project as open source, and choose a license that matches your intended use and distribution terms.

---

**Developed under Systematic Biologic**  
*Visualize DNA. Explore sequence. Connect structure with information.*
