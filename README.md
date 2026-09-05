# OrderStatus-Classifier-Dashboard

An interactive Streamlit dashboard for classifying e-commerce order status (`Cancelled`, `Returned`, `Pending`, `Shipped`, `Delivered`) using a Logistic Regression baseline model. Upload any similarly-structured dataset, configure preprocessing options, train the model, and download the results — all from the browser.

## Features

- 📤 Upload your own CSV or Excel dataset
- 🔍 **Data Understanding** — shape, dtypes, missing values, duplicates, statistical summary, target class distribution
- 🧹 **Preprocessing** — configurable identifier-column dropping, missing-value handling, automatic numeric/categorical feature detection
- 🏋️ **Train/Test Split & Training** — adjustable test size, random state, and model hyperparameters; Logistic Regression wrapped in a leak-safe `scikit-learn` pipeline (median/most-frequent imputation, scaling, one-hot encoding)
- 📊 **Evaluation** — accuracy, precision, recall, F1 score, full classification report, confusion matrix plot
- 💾 **Download** — trained model (`.pkl`), evaluation results (`.txt`), and confusion matrix (`.png`)

## Project Structure

```
OrderStatus-Classifier-Dashboard/
├── streamlit_app.py      # Main Streamlit dashboard
├── requirements.txt      # Python dependencies
└── README.md
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/OrderStatus-Classifier-Dashboard.git
cd OrderStatus-Classifier-Dashboard
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the app

```bash
streamlit run streamlit_app.py
```

The app will open in your browser at `http://localhost:8501`.

### 4. Use it

1. Upload your dataset (CSV or Excel) from the sidebar.
2. Select the target column and any identifier columns to drop.
3. Adjust the test size, random state, and `max_iter` if needed.
4. Go to **Train/Test & Training** and click "Run train/test split + train model".
5. Check results in **Evaluation**.
6. Download the model, report, or confusion matrix from **Download**.

## Dataset

The dashboard was built around a synthetic e-commerce order dataset with a 5-class, well-balanced target column (`OrderStatus`), but it generalizes to any tabular classification dataset — just point it at your file and pick the right target column.

## Model

- **Algorithm:** Logistic Regression (multinomial baseline classifier)
- **Preprocessing:** `ColumnTransformer` with median imputation + `StandardScaler` for numeric features, most-frequent imputation + `OneHotEncoder` for categorical features
- **Leakage prevention:** all preprocessing is fitted only on the training split, inside the pipeline

## Author

Aryan — AI/ML Internship Project

## License

MIT
