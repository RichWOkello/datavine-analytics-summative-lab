# GitHub repository setup

GitHub profile: **[Richard Okello (@RichWOkello)](https://github.com/RichWOkello)**

## Recommended repository details

**Repository name**

`datavine-analytics-summative-lab`

**Description** (paste into the GitHub repository's *Description* field)

> Machine learning projects in Python: PCA and tuned k-NN wine classification, PCA-based feed similarity, and K-Means/GMM clustering.

**Topics** (add in the repository's *About* panel)

`python` · `machine-learning` · `data-science` · `jupyter-notebook` · `scikit-learn` · `pca` · `knn` · `k-means` · `gaussian-mixture-model` · `eda`

**Visibility:** Public, if publication of the coursework and supplied datasets is permitted. Otherwise, use Private.

## Upload from the GitHub website

1. Sign in to [@RichWOkello](https://github.com/RichWOkello) and create a new repository at <https://github.com/new>.
2. Enter the suggested name and description above. Keep **Initialize with a README** unchecked, because this folder already has one.
3. Choose **Add file → Upload files**, and upload the **contents** of the extracted `datavine-analytics-summative-lab` folder rather than the ZIP file itself. Hidden `.github` and `.gitignore` files must also be included.
4. Commit the changes. The `README.md` will automatically display on the repository home page.
5. Confirm that `DataVine_Analytics_Summative_Lab.ipynb` displays its saved outputs and that the GitHub Actions notebook check succeeds.

## Upload from Git (recommended for hidden files)

Open a terminal **inside the extracted repository folder** and run:

```bash
git init
git add .
git commit -m "Add DataVine machine learning projects"
git branch -M main
git remote add origin https://github.com/RichWOkello/datavine-analytics-summative-lab.git
git push -u origin main
```

The remote address above becomes usable once the repository has been created under the `RichWOkello` account. GitHub may prompt for authentication. No existing repository is modified by the files in this ZIP.

**Publication note:** Verify that the course's academic integrity rules and dataset licensing allow a public repository before enabling public visibility.
