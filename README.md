# Stress-Detection-in-PINN-Model
Project Summary: Using chest data from a fitness device to detect stress. Then create a neural network model to predict high stress levels based on ECG, EDA and respiratory features.

Kaggle WESAD Dataset:

https://www.kaggle.com/datasets/orvile/wesad-wearable-stress-affect-detection-dataset/data 

Code process step by step:

1. Upload WESAD dataset directly from Kaggle. 

- Download necessary packages to begin the process.  

- Create KPI keys in Jupyter notebook that will connect directly to Kaggle website dataset and import into my code.  

2. Data Cleaning & Preparation 

- There are two types of data available for each data subject: chest and wrist.  

- I compared the chest and wrist to see which dataset has more available, and less null values. Chest data was the best dataset to focus on for my baseline and PINN models. 

- Begin pre-processing steps by downsampling each feature to their respective rates. 

ECG – 250 Hz 

EDA – 8 Hz 

Respiratory – 50 Hz 

- Next, segment the data into 60 second windows with 50% overlap. 

- Label each signal/feature in the dataset and check for any null values before building my baseline models. 

- The final step in the data pre-processing process is to create a combined features data frame and observe statistical summary (max, min, mean, standard deviation, etc.) 

3. Feature extraction 

- Extract basic features in chest data for ECG, EDA, and respiration segments. These three segments were finalized by my mentor, Dr. Lee, to get an accurate prediction from the model. 

4. Baseline Models 

- Created 4 baseline models to compare the accuracy scores to the final PINN model.  

Logistic Regression  

Random Forest Classifier 

XGBoost 

Neural Network Baseline 

5. PINN Model data processing  

- Define input layers for each feature extracted to accommodate their data structure.  

- Each feature is processed by its own 1D Convolutional Neural Network (1D-CNN).  This helps capture local patterns efficiently.  

6. PINN Model Architecture 

- Following the 1D-CNN layers, the output for each feature branch is fed into a Bidirectional LSTM layer. LSTMs are a type of neural network that captures a long-range temporal   dependency in time of sequential data. 

- Final output is a fused output that concatenates all feature dimensions. 

- The fused output is then passed through a fully connected dense layer with 128 units, which processes the combined feature before the final classification. 

7. Model training & execution 

- The multi-branch architecture allows the model to learn modality-specific features through the CNNs, capture context with BiLSTMs, and then integrate this information for a robust stress classification. 

8. PINN Model Evaluation & Accuracy Summary 

- Evaluate how the model performed using ROC-AUC scoring, and confusion matrix. 

- Created an AUC curve visual to show the accuracy and summarize how the model performed vs. Baseline models created previously. 
