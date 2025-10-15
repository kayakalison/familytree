# familytree
A visualization project that takes a SQL database of an adult softball league player data and transforms it into an interactive, panable and zoomable recruitment tree suitable for web access from either a desktop or mobile device.

<img width="1382" height="820" alt="demo screenshot" src="https://github.com/user-attachments/assets/8b7d3845-2300-4835-91db-7c9c696f041d" />

## Overview
This project uses player relationship data stored in a SQL database to generate an **undirected spring model** via the [Scalable Force-Directed Placement (sfdp)](https://graphviz.org/) engine in the **GraphViz** library. The output is an `.svg` vector image overlayed upon a pixel .jpg background that was originally visualized as a large-format (3' x 4') banner printed for a reunion event.

Due to the high resolution needed to preserve name readability, the static image file was too large for normal sharing or viewing. This repository provides a **pannable and zoomable** web viewer which used the [anvaka/panzoom](https://github.com/anvaka/panzoom) JavaScript library to create a version of the original banner that is accessible on both desktop and mobile platforms.

## How it Works
1. **Data Collection:** Player data is stored in a SQL database; database not included to protect individual privacy.
2. **Graph Generation:** A python script reads the data and generates an undirected spring model using the `sfdp` layout engine for large-scale graphs; jupyter notebook included in the reference folder.
3. **Image Generation:** The sfdp vector image was cleaned up manually, the founders and super recruiter circles were exchanged for apple and flower shapes, a title and legend were added, and the resultant imagery was overlaid on top of a background image rendered in Studio Ghibli style.
4. **Interactive Viewer:** The finished background and vector imagery are rendered in a web page with JavaScript-based pan and zoom (using `panzoom`).

## Database Schema
<img width="1252" height="305" alt="dbschema" src="https://github.com/user-attachments/assets/ce7b5bfd-83c6-45c6-b563-c8dcb50764e2" />

## Project Structure
```
├── data/
│ └── sauceball.db # Original SQL database (NOT INCLUDED)
├── reference/
│ └── TreeGeneration.ipynb # Jupyter Notebook to build the GraphViz model
│ └── sauceballtree.afdesign # Affinity Design 2 file for original graphic
│ └── familytree.png # Output from Jupyter Notebook file
│ └── familytree.svg # Output from Jupyter Notebook file
├── index.html # Interactive web viewer
├── sauceballtree.svg # Vector image layer
├── background.jpg # Background pixel image layer
├── README.md
```

## Live Demo
To view the interactive banner, open [https://kayakalison.github.io/familytree/index.html](https://kayakalison.github.io/familytree/index.html). No build or server is required—the viewer runs entirely in the browser.

## Notes on Privacy
To protect individual privacy, the original database has been omitted from this repo and the text in the vector image has been converted to curves (and is therefore not searchable). With these steps taken no specific personally identifiable information (PII) is being shared. Additionally, an opt-out button is included in case any individual wishes to have their name removed from the tree.

## Licensing
This project includes or builds upon the work of the following:

- **Visual Design and Artwork**  
  Vector and pixel layer artwork as well as overall banner design are © 2025 Alison Krauskopf and released under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

- **[anvaka/panzoom](https://github.com/anvaka/panzoom)**  
  Lightweight JavaScript library enabling smooth pan and zoom behavior on DOM and SVG elements.  
  License: MIT

- **[GraphViz](https://graphviz.org/)**  
  Open-source graph visualization software used for generating the force-directed graph layout via the `sfdp` engine.  
  License: Eclipse Public License 1.0

If you use or redistribute this project, please follow the respective license terms and provide appropriate credit.

## Acknowledgements
Thanks to Dana Myers Roberge, Mark Seto, Barry Erickson, Mia Honts Mar and anyone else who chipped in to help source the data that is foundational to this work – this project wouldn't exist without your input!
