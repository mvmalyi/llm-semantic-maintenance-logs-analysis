# Semantic Reliability Analysis of Wind Turbine Maintenance Logs using Large Language Models

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![DOI](https://zenodo.org/badge/1064032049.svg)](https://doi.org/10.5281/zenodo.17209085)  [![arXiv](https://img.shields.io/badge/arXiv-2509.22366-b31b1b.svg)](https://arxiv.org/abs/2509.22366)
 
 
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mvmalyi/) [![ORCID](https://img.shields.io/badge/ORCID-A6CE39?logo=orcid&logoColor=white)](https://orcid.org/0000-0002-1503-9798) [![ResearchGate](https://img.shields.io/badge/ResearchGate-00CCBB?logo=researchgate&logoColor=white)](https://www.researchgate.net/profile/Max-Malyi) [![Google Scholar](https://img.shields.io/badge/Google_Scholar-4285F4?logo=googlescholar&logoColor=white)](https://scholar.google.com/citations?user=FgcRBeUAAAAJ)

An open-source, reproducible framework demonstrating how Large Language Models (LLMs) can be used for complex semantic analysis of unstructured wind turbine maintenance logs. This project moves beyond simple classification to generate deeper reliability insights, such as identifying failure modes, inferring causal chains, and uncovering site-specific operational patterns to enhance data-driven O&M in the wind energy sector. 

This repository contains the full workflow as supplementary materials for the paper:
> Malyi, M., Shek, J., Biscaya, A., (2025). *Semantic Reliability Analysis of Wind Turbine Maintenance Logs using Large Language Models*. (To be published).


## About The Project

A wealth of operational intelligence is locked within the unstructured free-text of wind turbine maintenance logs, a resource largely inaccessible to traditional quantitative analysis. This project introduces an exploratory framework that uses state-of-the-art LLMs as an analytical tool, or "reliability co-pilot", to synthesise this textual data and generate actionable, expert-level hypotheses.

The framework is designed to be:
* **Reproducible:** All analytical workflows are contained within Jupyter notebooks with clear instructions and structured prompts.
* **Flexible:** The prompt engineering methodology can be easily adapted for different analytical tasks and datasets.
* **Insight-Oriented:** The analysis moves beyond data structuring to focus on hypothesis generation, root cause analysis, and uncovering nuanced operational patterns.


## Structure

The entire workflow is documented within the two primary Jupyter notebooks. The analysis is designed to be run sequentially.

1.  **Data Preparation:**
    Overview the cells in `1_data_cleaning.ipynb` to understand the pre-processing steps and how the analytical cohorts were created. Note that the original raw data is not provided due to commercial sensitivity; this notebook is for methodological transparency.

2.  **Semantic Analysis:**
    Open and run the cells in `2_processing_log.ipynb`. This notebook contains the prompts, LLM outputs, and Python code for all four analytical workflows:
    * Failure Mode Identification
    * Causal Chain Inference
    * Comparative Analysis
    * Data Quality Audit


## License

Distributed under the MIT License. See `LICENSE` for more information.


## Contact

Max Malyi - Max.Malyi@ed.ac.uk

Project Link: [Semantic Reliability Analysis of Wind Turbine Maintenance Logs using Large Language Models](https://github.com/mvmalyi/llm-semantic-maintenance-logs-analysis)
