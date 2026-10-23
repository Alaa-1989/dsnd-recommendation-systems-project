# Recommendation System - IBM Community

This project develops article recommendation systems using user interaction data from the IBM Watson Studio platform.

The workflow includes exploratory data analysis, rank-based recommendations, user-user collaborative filtering, content-based recommendations, matrix factorization, implementation tests, and discussion of recommendation evaluation.

## Getting Started

The project can be run locally using Python and Jupyter Notebook. Follow the steps below to create an isolated environment and install the required dependencies.

### Prerequisites

Make sure the following are available:

- Python 3.14.6
- pip
- A local terminal or command-line interface

Verify Python and pip using:

```bash
python3 --version
python3 -m pip --version
```

### Dependencies

The project uses:

- Python 3.14.6
- pandas 3.0.6
- NumPy 2.4.6
- Matplotlib 3.11.2
- scikit-learn 1.9.1
- Jupyter Notebook 7.6.0
- nbconvert 7.17.1

Package versions are specified in `requirements.txt`.

The `sys` and `subprocess` modules are included with Python. The supplied `project_tests.py` module is loaded from the project directory.

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Alaa-1989/dsnd-recommendation-systems-project.git
   ```

2. Navigate to the notebook directory:

   ```bash
   cd dsnd-recommendation-systems-project/starter
   ```

3. Create a virtual environment:

   ```bash
   python3 -m venv .venv
   ```

4. Activate the virtual environment:

   **macOS / Linux**

   ```bash
   source .venv/bin/activate
   ```

   **Windows**

   ```powershell
   .venv\Scripts\activate
   ```

5. Upgrade pip:

   ```bash
   python -m pip install --upgrade pip
   ```

6. Install the project dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

7. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

8. Open `Recommendations_with_IBM.ipynb` and run the cells from top to bottom.

Keep the supplied data and test reference files in their original locations so that the notebook can access them.

## Project Workflow

The notebook follows five main stages:

1. **Exploratory Data Analysis**
   - Inspect the dataset and identify missing values.
   - Replace missing emails with a shared `unknown_user` identifier.
   - Examine user activity and article popularity.
   - Calculate descriptive statistics for recorded interactions.

2. **Rank-Based Recommendations**
   - Rank articles by their total interaction counts.
   - Retrieve the most popular article titles and IDs.
   - Provide initial recommendations for users without interaction history.

3. **User-User Collaborative Filtering**
   - Build a binary user–article matrix.
   - Calculate cosine similarity between users.
   - Recommend articles from similar users.
   - Exclude previously viewed articles and duplicate recommendations.
   - Apply additional ranking rules to prioritize recommendations.

4. **Content-Based Recommendations**
   - Transform article titles using TF-IDF.
   - Reduce dimensionality using TruncatedSVD.
   - Examine the inertia curve and select 50 KMeans clusters.
   - Recommend articles from the same cluster, ranked by distinct-user counts.

5. **Matrix Factorization**
   - Apply SVD to the user–article matrix.
   - Examine reconstruction accuracy, precision, and recall.
   - Select 200 latent features as an initial configuration.
   - Recommend similar articles using cosine similarity in the latent space.
   - Discuss evaluation methods, limitations, and hybrid recommendations.

## Dataset and Main Results

The dataset contains:

- **45,993** recorded user–article interactions.
- **714** distinct articles.
- **17** missing email values, replaced with `unknown_user`.
- **5,149** user identifiers after handling missing emails, including the shared unknown-user identifier.

User activity and article popularity are highly right-skewed. The median number of interactions per user is **3**, while the maximum is **364**.

Article **1429**, *use deep learning for image classification*, is the most frequently accessed article, with **937 interactions**.

Implementation tests check the expected outputs of the recommendation functions. Further evaluation on held-out interactions and through online experiments would be needed to assess recommendation quality.

## Project Instructions

The project files include:

- `Recommendations_with_IBM.ipynb`: Completed notebook containing analysis, recommendation functions, tests, and discussion.
- `Recommendations_with_IBM.html`: Exported notebook containing saved outputs and figures.
- `Recommendations_with_IBM-zh.ipynb`: Additional notebook included with the Udacity starter materials.
- `data/`: Dataset used by the project.
- `project_tests.py`: Supplied validation functions.
- `top_5.p`, `top_10.p`, and `top_20.p`: Reference files used by the tests.
- `user_item_matrix.p`: Supplied user–article matrix reference file.
- `requirements.txt`: Package versions required to reproduce the project environment.
- `README.md`: Project documentation and execution instructions.

### HTML Export

Save the notebook before exporting it:

```bash
python -m nbconvert --to html Recommendations_with_IBM.ipynb
```

Open `Recommendations_with_IBM.html` in a web browser to view the exported report.

## Project Structure

```text
starter/
├── data/
│   └── user-item-interactions.csv
├── Recommendations_with_IBM.ipynb
├── Recommendations_with_IBM.html
├── Recommendations_with_IBM-zh.ipynb
├── project_tests.py
├── top_5.p
├── top_10.p
├── top_20.p
├── user_item_matrix.p
├── requirements.txt
└── README.md
```

## Built With

### Core Tools

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- scikit-learn

### Text Processing and Clustering

- TfidfVectorizer
- TruncatedSVD
- Normalizer
- KMeans

### Recommendation Methods

- Popularity-based ranking
- User-user collaborative filtering
- Content-based recommendations
- SVD-based article similarity
- Cosine similarity

### Evaluation

- Supplied Udacity validation tests
- accuracy_score
- precision_score
- recall_score

Precision@K, Recall@K, and A/B testing are discussed as possible future evaluation methods; they are not implemented in this notebook.

## Acknowledgments

- Udacity — Starter notebooks, dataset, validation materials, and project guidance.
- Python scientific computing libraries and scikit-learn — Data analysis and recommendation implementation tools.

## Author

Alaa Alaboud — Data exploration, recommendation system implementation, testing, results interpretation, and documentation.