### Applied Machine Learning Projects
<br>
Currently delving into the study of Computer Science, with a specialization area of applied machine learning as it relates to data analytics. My current curriculum consists of *Artificial Intelligence*, and *Programming Machine Learning Applications*. 

While the current state of software engineering has been well-entrenched and established for decades with best-practices in place, the field of data science is still in its infancy stages. There is a certain attraction to this new sub-field, with plenty of room to evolve as its best-practices and methodologies are still in early fluid development. There is also an analytical aspect to it, requiring professional intuition and extra mathematical savvy, on-top of the regular CS skillset.

-----
1. [**Experimentation With Different Structural Changes and Their Resulting Effects on the Performance of a Multilayer Perceptron Classifier.**](https://ericnewnam.github.io/sklearn-MNIST-MLP-various.html)
<br><br>
The MLP classifier is an algorithm that leverages many artificial "neurons" in its construction, configured in multiple layers. We will execute a series of structured, orderly changes and observe the effects on certain metrics, while gaining an intuitive understanding of the results when invoking certain high-level, or "hyper" parameters. We will plot the changes in resulting accuracy as a function of the parameter settings.

   Each iteration of the above settings will be run with different numbers of hidden layers, from 1 to 9: 
   - *L1 = 200, L2 = 500, L3 = 500, L4 = 400, L5 = 300, L6 = 200, L7 = 200, L8 = 100, and L9 = 100.*
<br><br>
2. [**Which Features Are King? An Analysis of Different House Characteristics on the Resulting Price in King County USA.**](https://ericnewnam.github.io/sas-king-county-report.html)
<br><br>
King County encompasses Seattle, WA. The goal of the study was to find clear correlations between certain features of the King County house sales dataset, and the resulting house price values. Would it be possible to fit a predictive model using regression analysis to predict, with a minimum of error, the dollar value? Were the features of _lot area, being on the waterfront_, and _having a large number of rooms_ the main features driving a higher house selling price? This was a hypothesis going into the study. <br><br>
The study began by re-encoding certain features and performing random sampling to get 1000 observations from the total dataset. The _Price_ feature was also log-transformed after analyzing its distribution. The model was fitted and iteratively improved, then validated with an 80/20 train to test split, examining the resulting performance and error. The model was also validated with a 5-fold cross validation, showing good performance with out-of-sample data.
<br><br>
3. [**An Exploratory Analysis of a Consumer Electronics Dataset with K Nearest Neighbors and K Means with Data Preprocessing.**](https://ericnewnam.github.io/KNN-experiments-with-KMeans.html)
<br><br>
We are given a csv file of 10,000 observations from a consumer electronics department. The purpose of this study is to exercise some dataset preparation / pre-processing and the use of various querying options and techniques such as Boolean indexing from within the framework of pandas and NumPy arrays.

   Before we begin, we will need to explore the dataframe and actively seek out missing, invalid, and abnormal values within our observations. 

   We will then explore the data through queries, and also try to discern patterns through Collaborative Filtering and some clustering.
<br><br>
