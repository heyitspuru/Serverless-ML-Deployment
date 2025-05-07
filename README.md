Welcome to the repository for our research:
"Serverless Deployment of an Ensemble Machine Learning Model for Diabetes Prediction: A Practical Study on Challenges and Cost Optimization."


📋 Project Overview
This project builds a complete machine learning pipeline for diabetes prediction using an ensemble of models (Neural Network, Random Forest, Gradient Boosting), hyperparameter tuning, and serverless cloud deployment using Google Cloud Functions.

We also systematically analyze practical deployment challenges, cold start latency, and serverless cost estimation.

🚀 Features
Data Preprocessing (Scaling, Splitting)

Hyperparameter Tuning using Keras Tuner

Ensemble Learning (NN + RF + GB Averaging)

Model Serialization (.keras and .pkl)

Serverless Deployment on Google Cloud Functions (GCF Gen2)

Cold Start vs Warm Start Performance Benchmarking

Cost Analysis for serverless inference

⚙️ Setup Instructions
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/heyitspuru/Serverless-ML-Deployment/tree/main Ml deployment.git
cd diabetes-serverless-ml
2. Install Required Packages
bash
Copy
Edit
pip install -r deploy_folder/requirements.txt
pip install keras-tuner
(Or use Google Colab for initial setup and model training.)

3. Train and Save Models
Use the model_training_and_tuning.ipynb to:

Preprocess data

Train models

Perform hyperparameter tuning

Save the models to deploy_folder/

4. Deploy to Google Cloud Functions (Gen2)
Use the deploy_to_gcf.ipynb script or run:

bash
Copy
Edit
gcloud functions deploy predict-diabetes-final01 \
  --region=us-central1 \
  --runtime=python310 \
  --trigger-http \
  --allow-unauthenticated \
  --source=gs://your-bucket-name/deploy_folder.zip \
  --entry-point=predict_diabetes_gcf \
  --memory=2GiB \
  --gen2 \
  --timeout=600s \
  --min-instances=1
5. Test the API Endpoint
Example payload:

python
Copy
Edit
import requests

url = "https://your-deployed-function-url"

payload = {
    "instances": [[
        0.038, 0.05, 0.061, 0.022,
        -0.044, -0.034, -0.043, -0.002,
        0.019, -0.017
    ]]
}

response = requests.post(url, json=payload)
print(response.json())
📊 Results Summary
Metric	Value
Best MAE (Ensemble)	47.95
Cold Start Latency	780 ms
Warm Start Latency	177 ms
Monthly Cost (Estimate)	~$0 (Free Tier)

📜 Research Paper
The complete Springer-format research paper is available in the /research_paper/ folder:

Title: Serverless Deployment of an Ensemble Machine Learning Model for Diabetes Prediction: A Practical Study on Challenges and Cost Optimization

🛠️ Tech Stack
Python 3.10

TensorFlow 2.x

Scikit-Learn

Keras Tuner

Flask + Functions Framework

Google Cloud Functions (Gen2)

Google Cloud Storage


📚 References
Refer to the full research paper for a detailed list of references cited in this work (15+ papers from top sources).

🤝 Acknowledgments
Google Cloud Research Credits

Open-source ML community (TensorFlow, Keras, Scikit-learn)

Springer Research Paper Format Resources

📢 License
This project is for educational and research purposes.
For any commercial use, please contact the authors.

📣
If you like this project, please give it a ⭐ on GitHub!
(Helps visibility and impact!)
