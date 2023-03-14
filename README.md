# Module-24- Technical Report

 # Predictors of Startup Success 
### Abstract
In recent years, numbers of startups have been on the rise. This industry plays a major role in the economic growth of many countries. With an estimate 1 out of 10 successes, most startups are struggling to find financing due to the perceived risk. In this project, we seek to understand the key factors capable of predicting a startups success which could help optimize the cash deployed and standardize the investment process. To do so, we have constructed several supervised machine learning models capable to predict a startups success and extracted the most important features affecting their prediction. The results have shown that the most important features investors and founders can increase the chances of success by establishing many business relationships. Furthermore, the positioning the company in ecommerce or the biotech industry will give a higher chance of success. For the financing of the business, founders should focus on the VC funding round and D round of financing. 

### Introduction
A Startup is a new company which seeks to grow, validate a scalable economic modeland and to develop an innovation capable of disrupting a sector. On the other hand, entrepreneurship refers to all new businesses including self-employment.  

Startups play a major role in the economic growth of many countries. They bring new ideas, spur innovation, create new technologies and are an important source of employment. Over the past two decades, the startup sector has grown exponantially in the number of new companies and in the volume of capital it attracts in investments.

Due to their high risks, startups face a high uncertainty and a minority of them go on to be successful. Their inherent risk and requirement for large amounts of capital make successful investment hard to come by. In fact, on average Venture Capital Funds (the main investors in startups) have a successful (IPO) investment rate of 1 out of 32. Due to the information asymmetry in private markets, investors have limited tools to objectively identify the qualities of a successful startup and their potential to attain "success".  

Before we continue, it is important to define "what is a successfull startup?". Often we have in mind sotries of "IPO unicorns" like Facebook or Amazon, but in fact startup success could be generalized the realization of an "Exit". These events can be intiated by an acquisition (M&A) or an IPO (Initial Public Offering)

### Project Overview
Although the sector is growing exponentially, many of startups fail. In fact, it is estimated that 9 out of 10 startups fail. So, what are the characteristics of startups which succeed? There are many factors that might play a role in this question: the founders and teams experience, the funding, the location, the product, the market and so on. What are factors that attract bigger companies into acquiring a startup? This report aims to investigate these questions using the [Startup Success Prediction](https://www.kaggle.com/datasets/manishkc06/startup-success-prediction) dataset available on Kaggle.  

### Problem Statement
The startup world requires a lot of decision making from the people involved, specially when dealing with situations of funding or acquisitions that will result in ownership changes. In these situations, the decision maker should have on hand all the information that can be provided with the amount of data available otday about companies, funding rounds and acquisitions.  

This project proposes a serie of supervised learning models that can forecast a startup success as well as a better understanding of the variables that most impact the acquisition or failure of a startup company. **Different supervised algorithms will be tested in order to compare our results and better understand the variables that most impact the outcome.**

You can access my Notebook [Here](https://github.com/LudovicBernard98/module-24---Report-Presentation/blob/main/Notebook%20-%20Capstone%20Report.ipynb).

### Performance Metrics
To evaluate the validity of each model we will use the True Positive Rate, False Positive Rate and the Area under the ROC Curve (AUC_ROC). True Positive rate and False Positive rates will be derived from the confusion matrix of our classifiers. We expect the number of companies that are acquired will be much smaller than those in operation or closed. Since we expect the dataset to be imbalanced such metric will be much more useful than accuracy.  If we were to use accuracy, our models could have a high score even though they are performing poorly when trying to retrieve the few companies that are more likely to be acquired.  

The ROC curve combines TPR(y-axis) and FPR (x-axis). In general, the AUC is a good metric for binary classification problems.

### Summary of the Results

Initially, we performed the analyis on 6 models to compare their scores and select the top 4 models to further our optimization of the parameters. These six models were: Logistic Regression, Support Vector Machines , Decision Tree Classifier, Random Forest Classifier, KNeighbors Classifier, AdaBoost Classifier and MLP Classifier. After our preliminary results, we decided to drop the Decision Tree and MLP Classifier.

Then, we optimized our models and got the following results:
- Logistic Regression ROC_AUC: 0.796
- Support Vector Machines ROC_AUC: 0.799
- Random Forest Classifier ROC_AUC: 0.810
- AdaBoost Classifier ROC_AUC: 0.8102

As we can observe, the four models have a similar roc_auc score. The highest score was from the AdaBoost Model with 0.8102 and Logistic Regression has the lowest score with 0.796. Since all scores were similar, we can confidently use all the model's important features in their prediction to better understand the factors impacting the success of a startup.

Results show the following:

**Random Forest & Adaboost**
- Classifier "AdaBoost" and "Random Forest" are models using regression trees. Using such models, it is normal to see the importance of One Hot Encoded variables to be much lower since the each decision in the tree takes the weights each variable for the decision node. Hence, the encoded variable is weighted against the entire dataset which inevitably leads to a lower strength in prediction importance since it mostly applies to a small subset of the data. Furthermore, it is very interesting to see that in the One Hot Encoded Variables in these models the feature has_VC still has a high importance than other encoded features of this class.
- Relationships consistenly appears in all 4 models as the most important feature for the prediction.
- Interestingly the total of funding in USD does not have a great impact on the success of a company. This challenges the optic that companies capable to raise a lot of money are successful. In fact, it carries almost no weight to the outcome of success.

**Logistic Regression & Support Vector Machines**
- The logistic Regression and SVM highlight as 2 most important features: "relationships" and "is_top500"
- The 2 highest sectors to be successful is "ecommerce" and "biotech"
- Furthermore, across the funding round it is interesting to note that the presence of a VC_round is very good to success but the importance of the following 2-3 rounds are less important. The last round "round_D" is the most important. In practice, successfully raising round_D is a great indicator of success since most of the market and product risk is behind the company. At this point, it is only a question of scaling and optimizing processes.
- It is interesting to note the state of california figures to be a less important predictor of success. In practice it is an important state for startups this is surprising to see the ecosystem does not translate in a higher success rate.

### 3. Conclusion - Results

In conclusion, the best predictor of succes for a startups are the "relationships" and in the one hot encoded variables: has_VC, has_round_D, is_biotech and is_ecommerce.

**Business Interpretation**
The business interpretation of these variables are as follows:
- relationships: as mentioned above the description of this variable is still unclear as the relationship could be toward clients or investors but in a general sense the larger the companies strategic network the more likely it is to succeed.
- has_VC: can be interpreted in practice as the presence of this first investor of institutional investor with a wide network and deep knowledge of the industry is an important step for a startups success.
- has_round_D is another important step showing a continued success from the company and ability to raise many rounds of investments. At this stage the company probably already has strong sales and is profitable or almost. Such stage in practice is usually much less risky to invest and the models seem to capture this concept.
- is_biotech and is_ecommerce are the most promising industries from this dataset. Biotech is a "Boom" or "Bust" industry that attracted a lot of attention in the last 10 years. In fact, these 2 industries have seen a lot of interest and seem to corroborate the excitement of investors by being a factor of importance in the prediction models. 

### 4. Next Steps & Improvements
- To improve this approach, it could be interesting to transform the dataset to accomodate the decision tree classifiers by ordinally encoding the funding rounds and state/location

- Finding a more thorought and a cleaner dataset would improve the results. Through EDA, it was clear that this dataset was very manipulated and did not provide a lot of description of their variables. Having the raw data with a clear description would greatly help the conclusions/inference of the results.

- Finding more data which better samples the entire startup market would provide a very different story. The dataset does not reasonable represent the real market which, for instance, has many more failures than success and should have a larger subset in california and Texas and in other industries. It is reasonable to think that these changes may leave the key findings highlighted the same.

- Previous researchers have tried to predict startups success from different types of data. To build their prediction models, some have combined financial data(similar to above) with news outlets about the companies using a natural language processor. This approach seems promising as the study conducted increase the TPR from 60% to 79.8%. This could be an interesting pathway to investigate and find ways to combine news (dynamic) with financial (static) data as a predictor of success.

- Other researcher have started from VC investment questionaires as the main features to investigate or lead to success. Including such data may provide a more complete picture to the problem.

- Furthermore, I believe other paths for feature engineering could be possible as highlighted above certain features although not correlated did not provide great insight or were similar to other variables in the dataset.