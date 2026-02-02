# 🚴‍♂️ Fahrradlicht Protokoll

<div align="center">

<!-- TODO: Add project logo (e.g., a bicycle light icon or relevant diagram) -->

[![GitHub stars](https://img.shields.io/github/stars/hyrvx/fahrradlicht-protokoll?style=for-the-badge)](https://github.com/hyrvx/fahrradlicht-protokoll/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/hyrvx/fahrradlicht-protokoll?style=for-the-badge)](https://github.com/hyrvx/fahrradlicht-protokoll/network)
[![GitHub issues](https://img.shields.io/github/issues/hyrvx/fahrradlicht-protokoll/issues?style=for-the-badge)](https://github.com/hyrvx/fahrradlicht-protokoll/issues)

**A comprehensive LaTeX document detailing the Bicycle Light Protocol.**

</div>

## 📖 Overview

This repository hosts the source code for the "Fahrradlicht Protokoll" (Bicycle Light Protocol) document, a detailed technical specification written in LaTeX. It aims to provide a clear and structured description of the protocol, including its requirements, technical specifications, and supporting datasheets.

The document serves as a foundational resource for understanding, implementing, and verifying bicycle light systems that adhere to the defined protocol.

## ✨ Key Contents

*   **Detailed Protocol Specification**: In-depth description of the bicycle light communication protocol.
*   **Comprehensive Requirements**: Documentation of functional and non-functional requirements in both English (`requirements.md`) and German (`requirements_de.md`).
*   **Integrated Datasheets**: References and potentially embeds relevant manufacturer datasheets from the `datasheets/` directory.
*   **Structured Document Layout**: Utilizes LaTeX for professional typesetting, automated cross-referencing, and consistent formatting across sections and chapters.

## 🖥️ Preview

<!-- TODO: Add actual screenshots of the compiled PDF document (e.g., a title page, a section with diagrams, a requirements table) -->
<!--
Example:
![Title Page](screenshots/title-page.png)
![Protocol Diagram](screenshots/protocol-diagram.png)
![Requirements Table](screenshots/requirements-table.png)
-->

## 🛠️ Tech Stack

**Document Processing:**
[![LaTeX](https://img.shields.io/badge/LaTeX-47A147?style=for-the-badge&logo=latex&logoColor=white)](https://www.latex-project.org/)

**Build & Automation:**
[![TeX Live](https://img.shields.io/badge/TeX%20Live-008080?style=for-the-badge&logo=tex&logoColor=white)](https://www.tug.org/texlive/)
[![Latexmk](https://img.shields.io/badge/Latexmk-A0522D?style=for-the-badge&logo=perl&logoColor=white)](https://ctan.org/pkg/latexmk)

**Containerization:**
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

## 🚀 Quick Start (Building the Document)

This project provides options to build the LaTeX document locally or using Docker for a consistent and reproducible environment.

### Prerequisites

To build the document locally, you need:
-   A complete **TeX distribution** (e.g., [TeX Live](https://www.tug.org/texlive/)). This typically includes `pdflatex` and `latexmk`.
-   **Perl**: `latexmk` is a Perl script, so Perl must be installed and accessible on your system.
-   **Docker**: (Optional) If you prefer a containerized build environment.

### Local Build

1.  **Clone the repository**
    ```bash
    git clone https://github.com/hyrvx/fahrradlicht-protokoll.git
    cd fahrradlicht-protokoll
    ```

2.  **Compile the LaTeX document**
    The `.latexmkrc` configuration file automates the compilation process using `latexmk`, ensuring all dependencies (like bibliographies, indices, multiple runs for cross-references) are handled correctly.
    ```bash
    latexmk -pdf main.tex
    ```
    Upon successful compilation, `main.pdf` will be generated in the root directory.

3.  **Clean up auxiliary files** (Optional)
    To remove all generated auxiliary files (like `.aux`, `.log`, `.bbl`, `.toc`), run:
    ```bash
    latexmk -c main.tex
    ```

### Docker Build

For a reproducible build environment, you can use Docker. It is assumed that a `Dockerfile` exists in the `docker/` directory to set up the necessary LaTeX compilation environment.

1.  **Clone the repository** (if not already done)
    ```bash
    git clone https://github.com/hyrvx/fahrradlicht-protokoll.git
    cd fahrradlicht-protokoll
    ```

2.  **Build the Docker image**
    Navigate to the `docker` directory and build the image. This will create an image named `fahrradlicht-protokoll-latex`.
    ```bash
    cd docker
    docker build -t fahrradlicht-protokoll-latex .
    cd .. # Return to the project root
    ```

3.  **Compile the LaTeX document using Docker**
    Run the Docker container, mounting the current project directory to compile `main.tex` within the container.
    ```bash
    docker run --rm -v "$(pwd):/app" fahrradlicht-protokoll-latex latexmk -pdf /app/main.tex
    ```
    This command will generate `main.pdf` in your local project root directory after the container finishes.

4.  **Clean up auxiliary files using Docker** (Optional)
    ```bash
    docker run --rm -v "$(pwd):/app" fahrradlicht-protokoll-latex latexmk -c /app/main.tex
    ```

## 📁 Project Structure

```
fahrradlicht-protokoll/
├── .gitignore               # Specifies intentionally untracked files and directories to ignore by Git.
├── .latexmkrc               # Configuration file for latexmk, automating the build process.
├── README.md                # The primary README file for this repository.
├── datasheets/              # Directory intended for storing technical datasheets referenced in the document.
├── docker/                  # Contains Dockerfile and related files for setting up a containerized build environment.
├── main.tex                 # The main LaTeX document entry point, includes other parts of the document.
├── pages/                   # Contains individual LaTeX chapters or sections that are included in `main.tex`.
├── requirements.md          # Project requirements documented in English markdown format.
├── requirements_de.md       # Project requirements documented in German markdown format.
└── resources/               # Static assets such as images, figures, or supplementary files used in the LaTeX document.
```

## ⚙️ Configuration

### `.latexmkrc`
The `.latexmkrc` file is crucial for streamlining the LaTeX compilation process. It customizes `latexmk` behavior by typically defining the default LaTeX engine (e.g., `pdflatex`), ensuring multiple compilation runs (necessary for resolving cross-references, bibliographies, and indices), and specifying output directories or cleanup options. This setup ensures that `latexmk -pdf main.tex` correctly builds the document with minimal manual intervention.

## 🤝 Contributing

While primarily a document repository, contributions such as corrections, clarifications, or additional content that enhances the protocol specification are highly welcome. Please feel free to open an issue to discuss proposed changes or submit a pull request directly.

### Development Setup for Contributors
To contribute, you should follow the [Local Build](#local-build) steps to set up your LaTeX development environment. Use a LaTeX editor of your choice (e.g., VS Code with LaTeX Workshop, TeXstudio, Overleaf for online collaboration) to make changes to the `.tex` files. Ensure your changes compile correctly using `latexmk -pdf main.tex` before submitting.

## 📄 License

This project currently has no explicit license specified in its repository metadata. Please contact the repository owner, [hyrvx](https://github.com/hyrvx), for licensing information regarding the contents of this repository.

## 🙏 Acknowledgments

*   The **LaTeX Project** for providing the powerful and versatile typesetting system that makes this document possible.
*   **John Collins** for `latexmk`, an indispensable tool that greatly automates and simplifies the LaTeX compilation workflow.
*   The broader **TeX community** for continuous support, development, and a wealth of packages and resources.

## 📞 Support & Contact

-   🐛 Issues: Feel free to report any issues, suggestions, or questions on the [GitHub Issues page](https://github.com/hyrvx/fahrradlicht-protokoll/issues).
-   📧 Contact: alexander.masser0@bulme.at<!-- TODO: Add a contact email or preferred communication channel if available -->

---

<div align="center">

**⭐ Star this repo if you find this protocol specification helpful!**

Made with ❤️ by [hyrvx](https://github.com/hyrvx)

</div>
```