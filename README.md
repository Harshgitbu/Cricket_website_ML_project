# Cricket End-To-End Website with ML integration

A Flask-powered web application for exploring and analyzing international cricket statistics. The project provides interactive visualizations, player and team profiles, and initial machine learning predictions for player performance.

## 📊 Features

### 1. Data Cleaning & Processing
- **Flattened CSV dataset** (`data/flattened_cricket_data.csv`) contains all player statistics across formats (Tests, ODIs, T20Is).  
- **Structured JSON** (`data/structured_cricket_data.json`) for quick lookup of player metadata.  
- Automated scripts for cleaning and converting numeric columns, handling missing or malformed entries.

### 2. Web Application (Flask)
- **Landing Page**: Default to Test format analysis with interactive viz embedded via iframes.  
- **Analysis Pages**: `/analysis/test`, `/analysis/odi`, `/analysis/t20` show top performers, custom visualizations.  
- **Players Tab**: `/players` displays a shuffled list of significant players (based on match count) with a search bar for name lookup.  
- **Player Profiles**: `/player/<ID>` shows personal info, format-specific batting & bowling tabs, cluster badges, and similar-player recommendations.  
- **Teams Tab** *(Coming Soon)*: Browse by country and view team rosters.

### 3. Machine Learning Module
- **Model Package**: `app/ML/ml_models.py` implements `CricketPerformanceModel` with:
  - Data cleaning & feature preparation pipelines.
  - Ensemble regression (Random Forest, Gradient Boosting, Linear Regression) for Test run predictions.
  - KMeans clustering to group players by performance metrics.
  - Similarity lookup via k-Nearest Neighbors.
  - `get_top_performers()` utility to retrieve top batsmen and bowlers per format.
- **Training Script**: `app/ML/train_models.py` trains and saves the model to `models/performance_model.pkl`.
- **Visualization Generator**: `app/ML/visualization_generator.py` produces:
  - Cluster scatter plots.
  - Model prediction comparison bar charts.
  - HTML report of model explanations.

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- pip (Python package manager)

### Installation
```bash
# Clone this repository
git clone https://github.com/your-username/cricket-insights.git
cd cricket-insights

# Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Running the App Locally
1. **Train or Load the ML Model** (one-time step):
   ```bash
   python3 -m app.ML.train_models
   ```
2. **Generate Visualizations**:
   ```bash
   python3 -m app.ML.visualization_generator
   ```
3. **Start the Flask Server**:
   ```bash
   python run.py
   ```
4. **Open Your Browser** and navigate to `http://127.0.0.1:8000/` to explore the app.

### Continuous Development Note
This project is a work in progress. While core features are functional, additional enhancements are planned:
- **Teams Tab**: Interactive browsing by country.
- **Advanced ML Features**: Role-specific models (batsman, bowler, all-rounder) with richer feature sets.
- **Interactive Scenario Explorer**: Real-time condition-based predictions (venue, opponent, form).
- **Deployment**: Containerization and hosted demo on a cloud platform.

## Contributing
Contributions and feedback are welcome! Please open an issue or submit a pull request with your enhancements or bug fixes.


---
_Last updated: 04-14-2025_
