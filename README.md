# Flowering Trees Dataset & Traits Analysis

## Overview
This project builds a structured dataset of flowering tree species and their ecological traits using data from botanical databases and open sources. It focuses on linking plant biodiversity with climate-related variables such as flowering patterns, and environmental conditions.

The goal is to support climate and biodiversity analysis through a clean, usable dataset that can be further expanded for GIS and machine learning applications like image search of flowering trees.

---

## Project Components

### 1. Dataset Construction
- Species list compiled from taxonomic backbone of World Flora Online. Used known flowering plant families to narrow down the families_dwc files to 418 files. 
- It included family, genus and other taxonomic variables like status and scientific name authorship.
- Ordered 21 TRY traits by numbers like 18 for plant height or 207 for flower color. It was a file with millions of rows so I used python to create a tree trait matrix which put the traits in different columns instead of rows.
- Ordered data from Global Tree Search so I could match it with the flowering plant families from WFO.

### 2. Data Processing
- Cleaning and standardization of species names
 - I used Angiosperm Phylogeny Website to get flowering plant families. There are 3 clades that flower. Eudicots, Monocotyledons and Magnoliids.
 - I then searched for those families in the WFO families_dwc file which is the taxonomic backbone. I combined these 418 files using python. I also kept the taxon rank to species, to only accepted taxonomic status and valid or conserved nomenclatural status. This filtering made the flowering_plant_families.csv file which is a clean version of the merged wfo families csv. 
- Tree Qualification
 - Then the flowering_plant_families.csv was matched with global tree search database to check which one of the WFO flowering plants qualitfy as a tree. The resulting file, flowering_trees.csv had about 53,000 out of 343,000 species that qualified. 

### 3. Analysis Notebook
- Exploratory data analysis in Jupyter Notebook (`flowering_traits.ipynb`)
- Assessment of data completeness
 - Almost 53,000 species of flowering trees was still a huge number. There were some tests ran to see whether random flowering trees exist in that dataset. They did in fact exist. 
- Trait distribution analysis
 - However, there was still a need to narrow down the number of species. For that, I merged the TRY tree_trait_matrix.csv with the flowering_trees.csv. It was done so because one of the 21 trait columns is called Plant Growth Form which tells us whether the plant is a shrub, herb, vine or tree etc.
 - That filter can be used to narrow it down more but there is a chance of blanks for some species or incomplete words which can cause discrepancies.
- POWO API does not let bulk scraping. If that were possible, I would have used it for native range and climate. 
- I will next use Wikipedia API to get native range and climate the trees grow in.
---

## Tech Stack
- Python 3.11
- pandas
- Jupyter Notebook
- CSV-based data pipeline

---

## Repository Structure