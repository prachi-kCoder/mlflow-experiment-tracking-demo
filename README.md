# mlflow-experiment-tracking-demo

# MLflow Experiment Tracking Demo: Basic Linear Regression

This repository showcases the fundamental capabilities of [MLflow Tracking](https://mlflow.org/docs/latest/llms/llm-tracking/index.html) for managing the machine learning lifecycle. It demonstrates how to log parameters, metrics, and artifacts (like trained models and plots) from multiple experiment runs.

## Project Goal

The primary goal of this mini-project is to provide a hands-on introduction to MLflow Tracking. We train a simple linear regression model multiple times with different (simulated) hyperparameters and log the results to MLflow, then visualize and compare these runs in the MLflow UI.

## Key MLflow Concepts Demonstrated

* **MLflow Tracking:** The core component for recording and querying experiments.
* **`mlflow.log_param()`:** For recording input parameters/hyperparameters of a run (e.g., `iterations`, `learning_rate`).
* **`mlflow.log_metric()`:** For logging quantitative performance metrics (e.g., `rmse`, `r2_score`).
* **`mlflow.<framework>.log_model()`:** For saving the trained machine learning model as an artifact.
* **`mlflow.log_artifact()`:** For storing additional output files, like plots or summary text, associated with a run.
* **MLflow UI:** The web interface to visualize, search, and compare experiment runs.
* **Remote Tracking (via `ngrok`):** How to configure the MLflow client to communicate with a remotely exposed MLflow Tracking Server (which is running locally in Colab and exposed by ngrok).

## How to Run This Project

This project is designed to be run in a Google Colab environment for ease of setup.

1.  **Open in Google Colab:**
    Click this button to open the notebook directly in Colab:
    [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/mlflow-experiment-tracking-demo/blob/main/mlflow_project_1_linear_regression.ipynb)
    *(Replace `YOUR_GITHUB_USERNAME` with your actual GitHub username once you've pushed the repo)*

2.  **Follow the Notebook Cells:**
    Execute each cell in the `mlflow_project_1_linear_regression.ipynb` notebook sequentially.

    * **Cell 1:** Installs required Python packages (`mlflow`, `scikit-learn`, `pyngrok`).
    * **Cell 2 (MLflow UI Setup):**
        * Starts the MLflow Tracking Server in the background within your Colab instance.
        * Uses `ngrok` to create a public URL to access the MLflow UI.
        * **You will be prompted to enter your `ngrok` authtoken.** Get one for free from [ngrok dashboard](https://dashboard.ngrok.com/auth/your-authtoken).
        * This cell will print the `https://...` URL for your MLflow UI. **Keep this URL handy!**
        * **Crucially**, this cell also configures the MLflow client to send all tracking data to this `ngrok` URL, which resolves issues with artifact logging when the server is remote.
    * **Cell 3 & 4 (Experiments):** These cells define and execute three different linear regression experiments, logging their parameters, metrics, and artifacts to the MLflow server.

3.  **Explore the MLflow UI:**
    After all cells have finished running, open the `ngrok` URL (from Cell 2's output) in your web browser.

    * You will see a list of the three experiment runs.
    * Select multiple runs (using the checkboxes) and click the "Compare" button to see their parameters and metrics side-by-side.
    * Click on any individual run to explore its detailed view, including:
        * **Parameters:** The `number_of_iterations` and `simulated_learning_rate` logged.
        * **Metrics:** The calculated `rmse` and `r2_score`.
        * **Artifacts:** Download the `trained_linear_model` (a folder containing the saved model), the `predictions_plot.png`, and the `model_details.txt`.

## Project Files

* `mlflow_project_1_linear_regression.ipynb`: The Google Colab notebook containing all the code and explanations for running the experiments.
* `requirements.txt`: Lists all Python dependencies needed to run the project.
* `mlflow.db`: The SQLite database file where MLflow stores the experiment tracking data locally. This file is included for easy demonstration, allowing direct `mlflow ui --backend-store-uri sqlite:///mlflow.db` if cloned locally.


## Future Work / Next Steps

* Explore more advanced MLflow Tracking features (e.g., logging metrics step-by-step for deep learning training).
* Introduce MLflow Projects for packaging code for reproducibility.
* Utilize MLflow Models for standardized model serving.
* Experiment with the MLflow Model Registry for versioning and lifecycle management of models.
