# 🎓 How to Use the R Markdown Report

This guide explains how to generate the professional molecular dynamics analysis report on your local RStudio installation.

## 📋 Quick Start

### Step 1: Install R and RStudio
- Download R from: https://cran.r-project.org/
- Download RStudio from: https://posit.co/download/rstudio-desktop/
- Install both applications

### Step 2: Install Required Packages

Open RStudio and run this in the R Console:

```r
# Install all required packages
packages <- c(
  "tidyverse",      # dplyr, ggplot2, readr, tibble
  "ggpubr",         # publication-ready plots
  "gridExtra",      # multi-panel layouts
  "scales",         # scaling functions
  "kableExtra",     # formatted tables
  "patchwork",      # plot composition
  "zoo"             # rolling averages
)

for (pkg in packages) {
  if (!requireNamespace(pkg, quietly = TRUE)) {
    install.packages(pkg)
  }
}

cat("✅ All packages installed successfully!\n")
```

### Step 3: Download Files

1. Download `MD_Complete_Report.Rmd` from GitHub
2. Place it in your working directory
3. Open it in RStudio

### Step 4: Load Your Data

In the **"1. Load Packages and Data"** section, replace the synthetic data generation with your actual CSV files:

```r
# OPTION A: Load from CSV files
rmsd <- read_csv("path/to/your/rmsd.csv")
rmsf <- read_csv("path/to/your/rmsf.csv")
gyrate <- read_csv("path/to/your/rg.csv")
energy <- read_csv("path/to/your/energy.csv")

# Ensure column names match:
# rmsd: "Time_ns", "RMSD_nm"
# rmsf: "Residue", "RMSF_nm"
# gyrate: "Time_ns", "Rg_nm"
# energy: "Time_ps", "Potential_kJmol"
```

### Step 5: Generate Report

Click the **"Knit"** button (or press `Ctrl+Shift+K` / `Cmd+Shift+K`)

Select output format:
- **HTML Document** (interactive, with table of contents)
- **PDF Document** (for printing)

Wait 1-2 minutes for the report to generate...

✅ **Done!** Your report will open automatically

---

## 📊 Expected Output

The script generates:

1. **MD_Analysis_Report.html** (or .pdf)
   - Interactive report with all analyses
   - Embedded figures at publication quality (300 DPI)
   - Clickable table of contents
   - Statistical summaries

2. **figures/** directory
   - `01_RMSD.png` - RMSD time series
   - `02_RadiusOfGyration.png` - Rg evolution
   - `03_RMSF.png` - Per-residue flexibility
   - `04_Energy.png` - Energy convergence
   - `05_Combined_Figure.png` - 2×2 publication figure

3. **figures/summary_statistics.csv**
   - Numerical summary table

---

## 🔧 Customization Options

### Change Data File Paths

Modify lines in the data import section:

```r
rmsd <- read_csv("C:/Users/YourUsername/data/rmsd_output.csv")
```

### Adjust Output Format

In the YAML header, change:

```yaml
output:
  pdf_document:          # or html_document
    fig_caption: yes
    toc: true
    number_sections: true
```

### Modify Colors

Change color codes in plot specifications:

```r
color = "#0072B2"    # Blue
color = "#009E73"    # Green
color = "#D55E00"    # Orange
color = "#CC79A7"    # Purple
```

### Adjust Figure Resolution

Change DPI in the setup chunk:

```r
knitr::opts_chunk$set(dpi = 300)  # or 150, 600, etc.
```

---

## 📁 Data Format Requirements

Your CSV files must have these columns:

### rmsd.csv
```
Time_ns,RMSD_nm
0.0,1.50
0.1,1.52
...
10.0,1.78
```

### rmsf.csv
```
Residue,RMSF_nm
1,0.35
2,0.38
...
324,0.42
```

### rg.csv (Radius of Gyration)
```
Time_ns,Rg_nm
0.0,2.05
0.1,2.06
...
10.0,2.10
```

### energy.csv (or Potential Energy)
```
Time_ps,Potential_kJmol
0,-285000
10,-285050
...
10000,-285300
```

---

## ⚠️ Troubleshooting

### "Package not found" error
**Solution:** Install missing packages:
```r
install.packages("package_name")
```

### "Cannot find file" error
**Solution:** Use absolute paths or check working directory:
```r
getwd()  # See current directory
setwd("C:/path/to/your/data")  # Change directory
```

### Figures not rendering
**Solution:** Check that input data has correct column names:
```r
head(rmsd)  # Verify structure
names(rmsd) # Check column names
```

### Report generation fails
**Solution:** Try rendering to HTML first (simpler):
```r
# In RMarkdown YAML:
output: html_document
```

---

## 🎯 Output Files for Publication

Once generated, you have:

- **HTML Report**: Share online or via email
- **PDF Report**: Submit for publication or printing
- **PNG Figures**: 300 DPI, suitable for all journals
- **Statistics Table**: For supplementary materials

---

## 📞 Support

If you encounter issues:

1. Check that all packages are installed
2. Verify CSV file format matches examples above
3. Ensure column names are exact (case-sensitive)
4. Try rendering to HTML format first (less dependencies)
5. Check the R Console for error messages

---

## 🚀 Advanced Options

### Render Programmatically

Instead of clicking "Knit":

```r
rmarkdown::render(
  "MD_Complete_Report.Rmd",
  output_format = "html_document",
  output_file = "My_MD_Analysis.html"
)
```

### Batch Processing Multiple Files

```r
simulation_systems <- c("System_1", "System_2", "System_3")

for (system in simulation_systems) {
  # Load system-specific data
  rmsd <- read_csv(paste0(system, "/rmsd.csv"))
  
  # Render report
  rmarkdown::render(
    "MD_Complete_Report.Rmd",
    output_file = paste0("Report_", system, ".html")
  )
}
```

### Export to PowerPoint (via HTML)

Generate HTML, then:
1. Open in browser
2. Print to file → "Save as PDF"
3. Or use Pandoc: `pandoc output.html -t pptx -o output.pptx`

---

**Happy analyzing! 🧬📊**
