# Election-Predictor
---------------------------

**Introduction**


The following analysis is an attempt to assess the relationship between electoral voting outcome and specific demographic and economic indicators within a given time period. The assessment is made by implementing various machine learning models for binary classification purposes: the target value is a binary value which indicates whether the elected party that year is either Democrat (0) or Republican (1).

**Methodology**


The dataset first goes through a scaling process in order to adjust large integer values to smaller floating values (representing percentages). Three methods have been implemented for this purposes: Min-Max Scaling, Standard Scaling (Z-Score) and Robust Scaling. Due to the considerable lack of performance from the last two models, only Min-Max Scaling has been used when adjusting the dataset later on during model training.
As the size of the dataset is relatively small (18,16), the splitting method used was Leave-One-Out Cross-Validation (LOOCV).
When choosing a binary classification model for our dataset, careful consideration is required because the dataset is small. Small datasets are prone to overfitting, and model performance may vary significantly. The models include: Logistic Regression, Support Vector Machines (VC), K Neighbours Classifier, Decision Tree Classifier, Naive Bayes and Random Forest classifier.

**Features and Target**


The dataset contains the following features:



- Year = year when the election took place. It is imported as the index of the DataFrame.
- male_vote: percentage of male voters
- female_vote: percentage of female voters
- white_vote: percentage of white Caucasian voters
- black_vote: percentage of Afro-American voters
- hispanic_vote: percentage of Hispanic voters
- other_vote: percentage of voters from other ethnic backgrounds
- voter_turnout: percentage of registered voters taking part to that year’s voting session
- inflation_growth: cumulative inflation growth over the four years prior that year’s election
- aliens_since_last_electio: total number of illegal aliens entering the country over the four years prior that year’s election
- recessions: : total number of recessions which took place over the four years prior that year’s election
- urban_pop: percentage of the urban population 
- unemp_rate: unemployment rate during election year
- violent_crime: violent crime rate for every 100,000 citizens
- property_crime: property crime rate for every 100,000 citizens
- prev_gov: ruling party prior to the election
- election_winner: party winning the election (the target value)



**Findings**



The first attempt was to employ all scaling methods and then determine the accuracy score for each model. The results are the following:

<img width="530" alt="image" src="https://github.com/user-attachments/assets/d022b6e9-623b-44dd-a0a3-39ffe4ad72a6" />




Due to its relative superior performance, only MinMax had been adopted throughout the rest of the analysis.
What followed was the assessment of the peformance of the same models by removing some of the features that may have no impact, or pehaps even a negative one, on the overall model performance. The results are the following:


1) No votes by gender:

<img width="521" alt="image" src="https://github.com/user-attachments/assets/e84f0b83-a398-451f-b13c-29f194368c35" />


Reuslts: The overall scores are wose than the original ones. It is recommended to keep the feature.


2) No votes by ethnic background:

<img width="517" alt="image" src="https://github.com/user-attachments/assets/c3c07486-8b18-46b9-8f53-d0370457799e" />


Results: SVC, Decision Tree and Random Forest performed decisively better, especially Decision Tree. Only KNN and Random Forest had a decline in performance. It is recommended to remove the features.
SS


3) No urban population:

<img width="518" alt="image" src="https://github.com/user-attachments/assets/1cdc9c50-0fbb-403e-9ec0-985cf021ca06" />


Results: Most models performed consderably wworse. It is recommended to keep the feature.


**Conclusion**


According the results give by the selected models, almost all of the data seems to impact positively the prediction performance, the only exception being the features realted to the votes based on ethnic backgrounds.
That being said, taking into consideration that the best performing model was the Decision Tree Classifer, with an overall score of 55.56% accuracy, it can hardly be said that the model is effecient in predicting the electoral outcome. Indeed, not much different from the flip of a coin. The unsatisfactory results may be due to a relative small dataset or a lack of relevant features. Further analysis is necessary.


