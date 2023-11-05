# Breast-Cancer-Recurrance-Rate-Predicitive-Algorithm
Machine Learning Algorithm predicting the possible recurrance rates of breast cancer based on seen and unseen data set. 
Developed and Designed By Sig Procak

DISCLAIMER: Please ensure to install Bayesian Optimization first before running the program in Google Colabs with !pip install bayesian-optimization

Acknowledgements

I would like to first extend my deepest gratitue to everyone involved in the assessment process for taking the time to scrutinize this submission. 
I earnestly welcome any constructive criticism, remarks or suggessions that may contribute to the refinement of this endeavour. 

Introduction

The program represents a meticulous fusion of machine learning, optimization techniques, and exploratory data analysis (EDA), all targeted at categorizing data into defined classes. 
Specifically, the ensemble employs Bayesian optimization to fine-tune a Keras-based neural network model. I will delve deeper into each segment, illuminating the purpose and functionality of each component.

Importing Required Libraries
The program begins with the importation of pivotal Python libraries essential for various tasks: data manipulation (pandas), machine learning (sklearn, keras), optimization (bayes_opt), 
data visualization (matplotlib, seaborn), and logging (logging). This rich tapestry of libraries signifies the comprehensive nature of the program.

Utility Functions

check_and_cast_column

Ensures a designated column's presence within a DataFrame and, when necessary, casts its data type. It acts as a guard against potential downstream errors.

determine_column_type

Strategically determines whether a column is categorical or numerical. It employs heuristics, such as assessing unique values and data types, to classify accordingly.

Data Loading, Preprocessing, and Exploratory Data Analysis (EDA)

The program dynamically sources data from an Excel file, exuding flexibility and adaptability.
Once the data is in place, it logs the available columns, seeking the user's input for the target column. 
Then, a comprehensive EDA is performed, visually presenting data distributions, correlations, and potential outliers using plots and statistical summaries. 
This allows for an informed understanding of the data and its intricacies.

Feature Engineering

Features are discerned and categorized based on the designated target column. The program also tackles label encoding, transmuting categorical data into a format digestible by machines.

Model Training with Bayesian Optimization

At the heart of the program is the objective function, tailored for Bayesian optimization.
It orchestrates the construction and training of the Keras neural network, fed parameters by the Bayesian optimization.

K-Fold Cross-Validation

To fortify the model's resilience and authenticity, K-Fold Cross-Validation is adopted. This strategy enriches data utilization and furnishes a rigorous model performance assessment.

Final Model Evaluation

Post-training, the model undergoes rigorous evaluation through metrics like accuracy, classification report, ROC-AUC curves, and more. TensorBoard is harnessed for real-time model training oversight.

Interpretive Value of ROC-AUC in this Program

The ROC-AUC metric stands out, owing to its resistance to class imbalance and its adeptness at consolidating both Sensitivity and Specificity into a coherent measure. In contexts like clinical diagnostics, where errant classifications could be detrimental, such a metric is indispensable. The program's ROC-AUC curve undergoes thorough analysis to ascertain an optimal balance between Sensitivity and Specificity, ensuring clinical reliability.

Model Evaluation Metrics from Console Output

From the console output, which was shared in the form of a screenshot, we observe several key metrics that provide a snapshot of the model's performance:

Accuracy: The accuracy of 0.862 signifies that the model correctly classified approximately 86.2% of the test data. 
This is a commendable score but should be analyzed alongside other metrics for a comprehensive understanding.

Classification Report: This report provides a more granular look into the model's performance:

Class 0: Boasts a precision of 0.88, recall of 0.93, and F1-score of 0.90.
Class 1: Demonstrates a precision of 0.81, recall of 0.72, and F1-score of 0.76.
The weighted average across classes further confirms the model's robust performance.

Deep Dive into Model Metrics

It's not just about the numbers. Understanding the implications of these metrics is crucial:

Precision: Measures the accuracy of the positive predictions. High precision indicates that false positive rates are low.

Recall: Evaluates the model's capability to detect all positive instances. In critical applications, a higher recall might be more desirable than precision.

F1-Score: Balances both precision and recall, providing a singular metric that encapsulates both attributes.

The histogram showcases the distribution of the feature 'inv-nodes' after it has been scaled. 
It's evident that the values are predominantly concentrated around -0.5, 1.0, and 1.5. 
Such a distribution pattern can provide insights into the nature of the data and how the feature values are spread. This could be indicative of the majority of data points falling under these specific ranges. Proper scaling ensures that all features have equal importance in influencing the model, avoiding any particular feature dominating due to its scale.

The learning curve provides a visual representation of the model's performance over successive training epochs. Two critical observations:

Training Accuracy: It begins high and experiences slight fluctuations. A consistently high training accuracy might suggest that the model is fitting well to the training data.

Validation Accuracy: It starts at a lower point compared to the training accuracy and undergoes more significant variations. The gap between the training and validation accuracies can be indicative of overfitting. It's crucial to ensure that the model is general enough to perform well on unseen data.

 Distribution of feature 'menopause' after scaling

The histogram depicts the scaled distribution of the feature 'menopause'. There is a pronounced concentration of data around the 0 and 1 markers. This distribution might be indicative of the majority of the data samples being categorized under these specific ranges for the 'menopause' feature. Understanding the distribution can provide clarity on how representative the dataset is concerning real-world scenarios and can inform decisions on potential data augmentation or collection.

Distribution of feature irradiat after scaling:

This distribution is essentially a histogram representing the count of data points at different intervals or bins.
The X-axis values, being scaled, suggest that you have employed some scaling technique like Min-Max Scaling or Standard Scaling (Z-score normalization). The presence of values around -1 and 1 usually indicates Z-score normalization.
We can see three major peaks:
A peak close to -1: This indicates that a certain subset of your data has values clustering around this scaled value.
A very prominent peak close to 0: This is where most of your data points lie. It's likely that this is the mean or median of your data (especially if Z-score normalization is applied).
A peak just above 1.5: This represents another subset of your data that has values clustering around this scaled value.
The distribution appears to be somewhat multimodal (having multiple peaks), suggesting that there may be distinct groups or clusters in your data for this feature.
Distribution of deg-malig:

Again, this is a histogram representing the count of data points for different values of the deg-malig feature.
The X-axis values seem to range from 1.00 to just under 3.00. It looks like the values of this feature might be discrete and perhaps ordinal in nature.
There are three notable peaks:
A smaller peak close to 1.25: This indicates a subset of the data with values clustering around this point.
A very prominent peak slightly under 2.00: This is where a significant portion of your data lies, making it the mode of this distribution.
A peak just under 3.00: This represents another subset of your data with values clustering around this value.
This distribution also appears to be multimodal. Given the peaks, this could be a categorical or ordinal variable with three major categories or levels. If this represents the degree of malignancy (as the name suggests), it could be categorized into three levels.
Conclusion:

The analysis of the distributions for the features irradiat and deg-malig provides crucial insights into the nature of the data, which is fundamental when predicting breast cancer recurrence rates.

Feature irradiat:

The distribution for the irradiat feature after scaling appears to be multimodal, suggesting multiple distinct clusters or groups within the data. Given the nature of the feature's name, this might represent whether a patient has undergone radiation treatment or not, or perhaps the intensity levels of such treatment. The presence of three distinct peaks might imply different levels or categories of irradiation.
A bulk of the data is clustered around the 0 value, suggesting a central tendency, possibly indicating that many patients had a standard or median level of irradiation.
Feature deg-malig:

The distribution of the deg-malig feature is also noticeably multimodal, implying distinct categories or levels. Given the potential interpretation of "degree of malignancy," these peaks might represent categorizations such as 'low,' 'medium,' and 'high' levels of malignancy.
The most prominent peak near the value 2.00 indicates that a significant portion of the observed cases falls within this malignancy category. If this represents a medium level of malignancy, it might mean that most patients in this dataset have a median level of cancer severity.
When predicting breast cancer recurrence rates, understanding the nature and distribution of these features is of paramount importance:

Interpreting the Model: Distinct clusters or groups in the features can imply different risk groups. For instance, patients with higher degrees of malignancy (deg-malig) might inherently have a higher risk of recurrence. Similarly, the level or type of irradiation treatment (irradiat) might be associated with varying recurrence risks.

Model Accuracy: Multimodal distributions can sometimes challenge certain machine learning algorithms, which assume feature normality. However, understanding these distributions allows for better preprocessing, feature engineering, and selection of appropriate algorithms, ultimately enhancing prediction accuracy.

Clinical Implications: Recognizing the prominence of specific categories, like the notable peak in deg-malig close to 2.00, can assist healthcare professionals in understanding prevalent risk levels in their patient population and tailoring treatments and follow-ups accordingly.

In essence, the distributions of these features offer a window into the heterogeneity of the patient dataset. 
For a model predicting breast cancer recurrence, such insights can guide both the technical aspects of model development and the clinical interpretations and interventions based on its predictions.
