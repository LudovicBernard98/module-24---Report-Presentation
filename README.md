# module-20---Initial-Report---EDA

 # Predictors of Startup Success 
### Introduction
A Startup is a new company (qualified when still at a project phase) which seeks to develop an innovation capable of disrupting sectors. While entrepreneurship refers to all new businesses, including self-employment and businesses that never intend to become registered, startups refer to new businesses that intend to grow and validate a scalable economic model.  

Startups play a major role in the economic growth of many countries. They bring new ideas, spur innovation, create new technologies and are an important source of employment. Over the past two decades, the startup sector has grown exponantially in number of new companies and in the volume of capital seeking to participate as investments.

Due to their high risks, startups face high uncertainty and a minority of them go on to be successful and influential. Their inherent risk and requirement for large amounts of capital make successful investment hard to come by. In fact, on average Venture Capital Funds (the main investors in startups) have a successful (IPO) investment rate of 1 out of 32. After adventuring myself in the field, it is clear that investors have limited tools to objectively identify the qualities of a successful startup and their potential to attain "success".  


Before we continue, it is important to define "what is a successfull startup?". Often we have in mind sotries of "IPO unicorns" like Facebook or Amazon, but in fact startup success could be generalized the realization of an "Exit". These events can be intiated by an acquisition (M&A) or an IPO (Initial Public Offering)

### Project Overview
Startup companiies are recently emerging and evolving more than ever. But still, many of them fail, in fact, 9 out of 10 startups fail. So, what are the characteristics of startups which succeed? There are many factors that might play a role in this question: founders and team experience, fundings, location, product, market and so on. Why some startups are acquired very early and others are not? Are ther maybe some factors that attract bigger companies into some startup acquisition? This report aims to investigate these questions using the [Startup Success Prediction](https://www.kaggle.com/datasets/manishkc06/startup-success-prediction) dataset available on Kaggle.  

### Problem Statement
The startup world requires a lot of decision making from the people involved, specially when dealing with situations of funding or acquisitions that will result in ownership changes. In these situations, the decision maker should have on hand all the information that can be provided with the amount of data available otday about companies, funding rounds and acquisitions.  

This project proposes a serie of supervised learning models that can forecast a startup success as well as a better understanding of the variables that most impact the acquisition or failure of a startup company. **Different supervised algorithms will be tested in order to compare our results and better understand the variables that most impact the outcome.**

You can access my Notebook [Here](https://github.com/LudovicBernard98/module-20---Initial-Report-EDA/blob/main/Notebook1--Data_Exploration.ipynb).

### Performance Metrics
To evaluate the validity of each model we will use the True Positive Rate, False Positive Rate and the Area under the ROC Curve (AUC_ROC). True Positive rate and False Positive rates will derived from the confusion matrix of our classifiers. Since we expect the dataset to be imbalanced such metric wil be much more useful than accuracy. We expect the number of companies that are acquired will be much smaller than those in operation or closed. If we were to use accuracy, our models would probably have a high score even though their will be performing poorly of retrieving the few companies that are more likely to be acquired.  

The ROC curve combines TPR(y-axis) and FPR (x-axis). In general, the AUC is a good metric for binary classification problems.

### Summary of the Results

Although all models have a similar roc_auc score, the highest score was from the AdaBoost Model with 0.810. Logistic Regression has the lowest score with 0.796. 

Preliminary results show the following:
**Decision Tree Based Classifiers**
- Classifier "AdaBoost" and "Random Forest" are models using regression trees. Using such models, it is normal to see the importance of One Hot Encoded variables to be lower since the decision tree decision takes weights each variable for the decision to the rest of the dataset hence a lower strength since it mostly applies to a small subset of the data. Furthermore, it is very interesting to see that in the One Hot Encoded Variables in these models the feature has_VC is the most important feature of this class.
- Relationships is the most consistent feature with a high prediction importance.
- The interestingly the total funding in USD does not have a great impact on the success of a company. This challenges the optic that companies capable to raise a lot of money or are seen as industry challengers by investors carries almost no weight to the outcome of success.

**Other Models**
- The logistic Regression and SVM highlight as 2 most important features: "relationships" and "is_top500"
- The 2 highest sectors to be successful is "ecommerce" and "biotech"
- Furthermore, across the funding round it is interesting to note that the presence of a VC_round is very good to success but the importance of the following 2-3 rounds are less important finishing with the presence of round_D as the most important
- interesting to note is the state of california figures to be a less important predictor of success. As an important state for startups this is surprising

### 3. Conclusion - Results

In conclusion, the best predictor of succes for a startups are the relationships, in the one hot encoded variables: has_VC, has_round_D, is_biotech and is_ecommerce.

**Business Interpretation**
The business interpretation of these variables are as follows:
- relationships: as mentioned above the description of this variable is still unclear as the relationship could be toward clients or investors but in a general sense the larger the companies strategic network the more likely it is to succeed.
- has_VC: can be interpreted in practice as the presence of this first investor of institutional investor with a wide network and deep knowledge of the industry is an important step for a startups success.
- has_round_D is another important step showing a continued success from the company and ability to raise many rounds of investments. At this stage the company probably already has strong sales and is profitable or almost. Such stage in practice is usually much less risky to invest and the models seem to capture this concept.
- is_biotech and is_ecommerce are the most promising industries from this dataset. Biotech is a "Boom" or "Bust" industry that attracted a lot of attention in the last 10 years. In fact, these 2 industries have seen a lot of interest and seem to corroborate the excitement of investors by being a factor of importance in the prediction models. 

### 4. Next Steps & Improvements

- I believe the main improvement for this project would be to find a cleaner dataset. Through EDA, it was clear that this dataset was very manipulated and did not provide a lot of description of their variables. Having the raw data with a clear description would greatly help the conclusions of this project.

- Finding more data which better sampled the entire startup market would provide, in my opinion, a very different story although the key findings highlighted remain reasonable for this setting.

- Previous researchers have tried to predict startups success from different types of data. To build their prediction models, some have combined financial data(similar to above) with news outlets about the companies using a natural language processor. This approach seems promising as the study conducted increase the TPR from 60% to 79.8%. This could be an interesting pathway to investigate and find ways to combine news (dynamic) with financial (static) data as a predictor of success.

- Other researcher have started from VC investment questionaires as the main features to investigate or lead to success.

- Furthermore, I believe other path for feature engineering could be possible as highlighted above certain features although not correlated did not provide great insight or were similar to other variables in the dataset.