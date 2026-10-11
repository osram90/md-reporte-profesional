# 📊 R Markdown Templates for Molecular Dynamics Analysis

This repository includes **two complete R Markdown templates** for professional molecular dynamics analysis, ready to knit to PDF or HTML.

## 📁 Files Available

### 1. **MD_Analysis_English.Rmd** (English Version)
Complete molecular dynamics analysis report in English with:
- ✅ RMSD (Root Mean Square Deviation) analysis
- ✅ Rg (Radius of Gyration) calculations  
- ✅ RMSF (Root Mean Square Fluctuation) per-residue flexibility
- ✅ Potential energy convergence analysis
- ✅ Publication-ready figures with ggplot2
- ✅ Statistical summaries and interpretations
- ✅ Code blocks integrated before/after visualizations

### 2. **MD_Analysis_Español.Rmd** (Spanish Version)
Análisis completo de dinámicas moleculares en español con:
- ✅ Análisis RMSD con fundamentación teórica
- ✅ Radio de giro y compacidad proteica
- ✅ Fluctuación por residuo (RMSF)
- ✅ Convergencia de energía potencial
- ✅ Figuras listas para publicación
- ✅ Tablas de resumen estadístico
- ✅ Interpretación científica completa

## 🚀 How to Use

### Requirements
```r
install.packages(c(
  "ggplot2",
  "dplyr",
  "readr",
  "ggpubr",
  "gridExtra",
  "scales",
  "patchwork",
  "kableExtra"
))
```

### Quick Start

#### Option 1: Knit in RStudio
1. Download the `.Rmd` file
2. Open in RStudio
3. Click **Knit** button
4. Select output format (PDF or HTML)

#### Option 2: Command Line
```r
# English version
rmarkdown::render("MD_Analysis_English.Rmd", 
                  output_format = "pdf_document")

# Spanish version
rmarkdown::render("MD_Analysis_Español.Rmd", 
                  output_format = "pdf_document")
```

#### Option 3: Load Data from CSV Files
Modify the data import section:
```r
# English
rmsd <- read_csv("path/to/rmsd.csv")
rmsf <- read_csv("path/to/rmsf.csv")
energy <- read_csv("path/to/energy.csv")

# Spanish
rmsd <- read_csv("ruta/a/rmsd.csv")
rmsf <- read_csv("ruta/a/rmsf.csv")
energia <- read_csv("ruta/a/energia.csv")
```

## 📊 Content Structure

Both templates include:

### 1. Data Import and Processing
- Standardized column naming
- Statistical summaries
- Data validation checks

### 2. Core Analysis Sections
- **RMSD Analysis**: Structural stability metrics
- **Radius of Gyration**: Protein compactness
- **RMSF Analysis**: Per-residue flexibility mapping
- **Energy Analysis**: Thermodynamic convergence

### 3. Visualizations
- Individual publication-ready figures
- Four-panel composite figure
- Confidence intervals and statistical annotations
- Professional styling with publication aesthetics

### 4. Tables and Statistics
- Summary statistics table (kableExtra formatted)
- Descriptive statistics with interpretation
- Formatted for publication

### 5. Interpretation and Conclusions
- Scientific interpretation of results
- Stability assessment criteria
- Recommendations for extended analysis

## 🎨 Figure Output Examples

All figures include:
- Professional color palettes
- Confidence intervals (±1 SD shaded regions)
- Statistical annotations
- Publication-ready quality (300 dpi)

### Figure Types Generated:
- Time series plots (RMSD, Rg, Energy)
- Area plots (RMSF profile)
- Composite multi-panel figures
- Statistical summary table

## 📖 Output Formats

### PDF Document
```r
output:
  pdf_document:
    fig_caption: yes
    toc: true
    number_sections: true
```

### HTML Document
```r
output:
  html_document:
    theme: flatly
    toc_float: true
    number_sections: true
```

Both formats produce publication-ready documents suitable for:
- Scientific papers
- Thesis chapters
- Conference presentations
- Research reports

## 🔬 Scientific Accuracy

All templates include:
- ✅ Correct mathematical formulas (RMSD, Rg, RMSF)
- ✅ Proper statistical analysis
- ✅ Equilibration time detection
- ✅ Convergence assessment
- ✅ Confidence interval calculation
- ✅ Professional scientific interpretation

## 💾 Data Requirements

Expected CSV file structure:

### RMSD Data
```
Time_ns,RMSD_nm
0.0,1.50
0.1,1.52
...
10.0,1.78
```

### RMSF Data
```
Residue,RMSF_nm
1,0.35
2,0.38
...
324,0.42
```

### Energy Data
```
Time_ps,Potential_kJmol
0,-285000
10,-285050
...
10000,-285300
```

## ✨ Key Features

- 🎯 **Publication-Ready**: Professional formatting and styling
- 📊 **Complete Analysis**: All standard MD metrics included
- 🔧 **Fully Customizable**: Easy to modify for your data
- 📚 **Bilingual**: Both English and Spanish versions
- 🎨 **Professional Aesthetics**: ggplot2 styling for publication
- 📈 **Statistical Rigor**: Proper statistics and confidence intervals
- 💻 **Reproducible**: All code visible and documented
- 🖨️ **Print-Ready**: PDF output optimized for printing

## 🎓 Learning Resources

Each template includes:
- Theoretical background for each metric
- Mathematical equations (LaTeX formatted)
- Code comments explaining each step
- Interpretation guidelines
- Best practices for MD analysis

## 📞 Support

For issues or questions about the templates:
1. Check the code comments in each section
2. Review the theoretical background sections
3. Verify your data format matches the expected structure
4. Ensure all required packages are installed

## 📄 License

These templates are provided under the MIT License for academic and research use.

---

**Generated with:** RMarkdown + ggplot2 + GROMACS
**Citation:** Include these templates as supplementary materials in your publications
**Last Updated:** October 2026

Happy analyzing! 🚀

