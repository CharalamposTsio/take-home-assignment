# take-home-assignment

# Matching System of Product Catalog

This repository contains my solution to the take home assignment. The goal is to create an automatic process of matching unstructured product descriptions to the correct SKU.
<img width="1194" height="202" alt="Screenshot 2025-11-26 at 11 33 13" src="https://github.com/user-attachments/assets/06ae21f0-a31c-4a35-8d3c-8f01348988cf" />


## 1. Setup & Installation 

First, in order to install/ prepare the project, you need to download (or clone) the repository. Then, install (pandas, numpy, scikit-learn, rapidfuzz, matplotlib, seaborn) libraries. After that, put the CSV files in the same place that they are located inside the notebook. Finally open the file assignment.ipynb, and execute the notebook.


## 2. Required files

Input files

- b_unstructured_descriptions.csv # free-text descriptions (Dataset A)

- b_product_catalog.csv # structured catalog (Dataset B) 

- validation_results.csv # manually created file with the correct SKUs for model evaluation

(Notebook: assignment.ipynb)

Execution of the notebook resulting in 

- matched_results.csv  # all predictions for the extracted attributes & top-3 SKUs

- performance_results.csv # overall accuracy & measures

- validation_sample.csv # described sample for validation (30 rows)

- error_analysis.csv # rows where the model did not match the correct SKU


## 3. How to execute the matching system

Open up/ run the notebook assignment.ipynb

Execute all cells from the top to the bottom


This will :


- clean/preprocess descriptions,


- extract attributes color, brand, and size,


- build TF-IDF vectors,


- report the 3 SKU matches that obtained high confidence scores,


- save all outputs to CSV files


## 4. Sample query example


When all definitions are successful in the notebook, it is possible to try out a custom description:

```python
test = "Looking for a navy cotton cardigan size M"

clean = clean_text(test)

row = pd.Series({
    "Unstructured_Description": test,
    "clean_text": clean,
    "color_extracted": extract_color(test),
    "brand_extracted": extract_brand(test),
    "size_extracted": extract_size(test)
})

match_description(row, top_k=3)
```


## 5. Troubleshooting

i. If the file was not found, then make sure that the CSV paths in the notebook follow the path structure of the folders.

ii. If there are missing modules , then install libraries
```python
pip install pandas numpy scikit-learn rapidfuzz matplotlib seaborn
```
iii. If there are encoding issues, then try loading CSVs with UTF-8
```python
pd.read_csv("file.csv", encoding="utf-8")
```

