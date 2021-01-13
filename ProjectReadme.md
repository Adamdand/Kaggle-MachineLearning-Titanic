Here is where you include:

  - Background on your code files
  
  The project involves investigating the survival rate of the passengers of the Titanic
  The data was pervided by the Kaggle Compitition, and the goal is to try to predict if a passenger will survive based on various features.
  Most of the features are self explanitory, but I would like to point out a couple of special note:
  
      if Survival = 0 : the passenger did NOT survive.
      if Survival = 1 : the passenger DID survive.
  
      Embarkment: C = Cherbourg, Q = Quenstown, S = Southampton.
  
  
  Some data in the features was in String format, so One-Hot-Encoder was used.
  
  After removing the un-needed columns and some null age rows, the data set was a little unbalanced (424 NonSurvivers, and 288 Survivers).
  To account for this, when the data was split into training and testing data, the y_enc data was stratified.
  
  Kaggle also supplied a csv file with the survival column excuded, however it was not necessary for me to use this, as I justmanuualy removed the column myself from the other file, and split it into training and testing data.
  
  - How to run your code, guide to install any additional packages
  
  Please run all of the cells in order, the necessary packages will be installed in the order that they are needed.
  The first few blocks of code are pre-made functions to calculate repeatedly needed algorythms.
  
  
  
  - Results, interpretation and reflection
  
  -RESULTS:
  
  -Please view MLProject.ipynb file in JupyterLab for Result Figures, Tables, Files, and Plots
  
  This code ran smoother than expected, and the final validation and testing scores are very high:
  
  Cross validation determined the following:
  
  SVC: Valdiation Score = 0.830 ; Training Score = 0.945
  Gradient Boosting: Valdiation Score = 0.830 ; Training Score = 0.948
  Logistic Regression: Valdiation Score = 0.828 ; Training Score = 0.929
  Random Forest: Valdiation Score = 0.812 ; Training Score = 0.999
  Gaussian NB: Valdiation Score = 0.457 ; Training Score = 0.622
  
  Then after running a Grid Search on each of the models, the following scores were obtained:
  
  SVC: Valdiation Score = 0.829 ; Training Score = 0.874
  Gradient Boosting: Valdiation Score = 0.828 ; Training Score = 0.997
  Logistic Regression: Valdiation Score = 0.828 ; Training Score = 0.929
  Random Forest: Valdiation Score = 0.836 ; Training Score = 0.988
  Gaussian NB: Thrown out
  
  
  
  -INTERPRETATION
  
  The Random Forest performed very well, with the highest validations scores.
  So I used Random Forest to further refine our accuracy/percision using various thresholds
  In the end, a nice balance was found, giving us a final survival F1 score of 75%, and a does NOT survive F1 score of 87%.
  Accuracy, precision and recall are all relativly high:
  
  Deos NOT Survive (precision = 0.84, recall = 0.87)
  Does Survive (precision = 0.80, recall = 0.70)
  and a Accuracy of 83%
  
  From further investigation with figures, it can be determined that young children and women were let on the life boats first, resulting in drastically more women and children surviving the incident.
  
  
  Also, lots of Class 3 passengers did not survive (~ 2.5 times more than class 1 and 2 passengers), however an equal amount of class 1,2 and 3 survived. This tells us that there simply are more class 3 passengers than any other type.
  But that the life-boats took an even number from each passenger class.

  It does appear as though the passengers whom embarked from "C" (Cherbourg) had a higher chance of survival, however, I stuggle to come up with an explination for this, appart from them maybe having more children or women ( a female birthday party or something) on board
  
  -REFLECTION
  
  Suprisingly, I was able to stay on track with my project proposal. The titanic code ran relatively smoothly when I applied Lab3 trechniques to it
  I was also able to impliment a couple extra firgures for analytical interpretation.
  
  it would be interesting to see how accurate out Machine Learning algorythms can predict the outcome of a massenger, if the "sex" column was removed from the feature list. Because currently, I beleive 'Sex' is the most impactful feature
  I tried to print out 'feature importance' in a nice plot, but I was having trouble with the output
  I removed blank "age" rows from the data set, this reduces our data set, however I thought the trade off of loosing some rows of data was worth maintaining the 'purity' of the data set by NOT averageing age values to fill in the blank's. However, I supposed before dropping these rows, I should had done the data analytics of the features that do not involved 'Age' first.
  