# Complete Machine Learning & Data Science

[TOC]

## Project Lifecycle

1. Data Collection

   - Source systems, flat files, data streams, etc.

2. Data modelling

   1. Problem definition
      - What problem are we trying to solve?
   2. Data
      - What data do we have? structured vs unstructured
   3. Evaluation
      - What defines success?
   4. Features
      - What features should we model?
   5. Modelling
      - What kind of model should we use?
   6. Experiments
      - What have we tried/what else can we try?

3. Deployment

   

   <figure>
    	<img src="C:\Users\nyoun\repos\ml-data-science\notes\ml-project-lifecycle.PNG"/>
   	<figcaption>Steps in a full machine learning project</figcaption>
   </figure>

   

## Problem Definition

### Types Of Machine Learning 

In order to ensure good results you must fit the proper ML type to the problem you are trying to solve. It's important to remember not every problem solution needs ML!

<ol>
    <li><span style='color: #007ba7;'>Supervised Learning</span></li>
    Data is labeled and the algorithm attempts to choose the correct label for new data. If wrong, it tries again. Sub-types:
    <ul>
      <li>Classification - is this data one thing or another e.g., is this person at risk of heart disease? Two flavors - binary (one of two options) or multi-class (more than two options e.g., what kind of dog breed?)</li>
      <li>Regression - predictive numerical guess e.g., How much will a house sell for based on characteristics (neighborhood, square footage, number of rooms, etc.)?</li>
    </ul>
    <li><span style='color: #007ba7;'>Unsupervised Learning</span></li>
    Suppose you work at an ecommerce company and the marketing department wants to figure out where to send an email campaign in order to sell a certain class of goods such as winter clothing. Given a list of customers and their corresponding past purchases, you can use unsupervised learning to divide and group the customer list into segments which can indicate likelihood to make a purchase of the goods. Dividing the list like this is called clustering. Recommendation engines can often start out as unsupervised learning problems.
    <li><span style='color: #007ba7;'>Transfer Learning</span></li>
    Using an existing ML model to inform another, related, problem type. For instance, say you had a problem where you wanted a system to identify cars & dogs in photos. If you already have a model which identifies cars then you can repurpose & fine-tune the model to also identify the dogs rather than building an entirly new model from scratch. This is important because training these models can be expensive due to the number of calculations required for good results.
    <li><span style='color: #007ba7;'>Reinforcement Learning</span></li>
    Training a model to perform a task and then rewarding or punishing the model based on the result. The reward/punishment can be as simple as incrementing/decrementing a score value with the end result being the highest score wins. This is what the famous DeepMind Go AI used. Although impressive it has yet to find many common applications in the business world.
</ol>
### Simple questionnaire to determine problem/learning type fit:

1. "I know my inputs and outputs" ==> ```Supervised Learning```
2. "I know my inputs but not sure of my outputs" ==> ```Unsupervised Learning```
3. "This problem is similar to something else" ==> ```Transfer Learning```



## Data

The more data the better!

* Structured
  * CSVs, database tables, flat files
* Unstructured
  * Images, video, audio

In the beginning of a project data is most commonly consumed statically (as in flat files or other basic forms) because creating the model may require experimentation in order to achieve the desired outcome. Once the model has been productionized the data source may either be exposed via API endpoints or it may be exposed to streams of data to analyze. 

For example, imagine a model trained to guess a stock price based on ingesting a real-time stream of news feeds.



<figure>
 	<img src="C:\Users\nyoun\repos\ml-data-science\notes\example-workflow-tooling.PNG"/>
	<figcaption>Heart disease prediction model example workflow</figcaption>
</figure>

## Evaluation

### ML Evaluation Metrics

| Classification | Regression | Recommendation |
| -------------- | ---------- | -------------- |
| Accuracy  | Mean Absolute Error (MAE)      | Precision at K |
| Precision | Mean Squared Error (MSE)       | |
| Recall    | Root Mean Squared Error (RMSE) | |



## Features

* Feature variables 

  Raw data points in the source data we use for analysis. Feature variables come in two flavors:

  1. Numerical - value is a number of some sort (e.g., weight, heart rate, chest pain)
  2. Categorical - one thing or another (e.g., gender, isSmoker)

* Target variables

  Values we are trying to predict

* Derived features

  Values we add to the above from existing data to augment the source data set (e.g., checking hospital timestamp in the row to create a "Visited in last year" categorical feature)

**Feature engineering** is the process of looking at different features of data and creating new ones/altering existing ones.

**Feature coverage** is the frequency at which a feature is present for each row of data in the dataset. An ideal dataset ensures every sample has data present for the same features. 

It is tempting to think feature engineering is only present for structured data (think tabular data rows/columns) but unstructured data has feature engineering as well. 



## Modelling

Based on our problem and data, which model should we use?



Choosing how to split your data is incredibly important. You split your data into the **3 sets**:

1. Training data - trains your model (70 - 80%)
2. Validation data - tune your model (10 - 15%)
3. Test Data - test & compare your model (10 - 15%)

Data split issues:

1. Data leakage 
   1. When some data from the training and test data sets overlap. This allows the model to 'peek' at the test data and tends to lead to overfitting.
2. Data mismatch
   1. When training data and testing data are different (e.g., datasets have different features) and tends to lead to underfitting.



Modelling has 3 parts:

1. Choosing & training a model

   a. uses the training data set 

   b.  As a general rule, if working with structured data decision trees and gradient boost models *tend* to work best. If working with unstructured data deep learning and transfer learning *tend* to work best.

   c. Goal: Minimize time between experiments! Iterating through experiments is important to find best fit. One optimization is to use a portion of your (large) training dataset at first to see results then expand to using the full dataset in a stepwise manner to evaluate the outcome. Make sure to compare apples-to-apples when analyzing experiments.

2. Tuning a model

   a. uses the training and/or validation data

   b. improving your model to fit your data by tuning the hyperparameters; remember a model's first results are not it's last. Example: imagine roasting a chicken in the oven at 300 for one hour. It comes out raw and requires more cook time with a poor result. The next time you cook it at 350. That is tuning the oven temperature hyperparameter across experiments to make the process more efficient.

3. Model comparison

   a. uses the test data

   b. A good model should show similar results between the training set performance and the test set performance.

   c. One best performance metric does not equal best model! There are many factors related to what is the best model including accuracy, time to train, time to output new values (predictions) which should all be driven by the needs of the business case. A 100% accurate model which takes a day to make a new prediction means nothing if 90% accuracy within one minute is the business use case.



Overfitting/Underfitting Troubleshooting

1. Underfitting - poor performance on training data

   a. try more advanced model

   b. increase model hyperparameters

   c. reduce amount of features

   d. train longer

2. Overfitting - great performance on training data, poor performance on test data

   a. collect more data

   b. try a less advanced model



## Experimentation

What have we tried/what else can we try? May include try a new model, change desired outputs, etc. Performed iteratively as needed until an acceptable result is achieved.



## Workbench Setup

* Using Miniconda rather than Anaconda 
  * Miniconda is a bare bones install with a language runtime and the ```conda``` package manager so it is essentially like a fresh ```npm``` project
  * Anaconda installs the runtime and tons of packages by default even if you don't use them
* Initialize project & dependencies
  * ```conda create --prefix ./env pandas numpy matplotlib scikit-learn```
  * dependencies are installed in the ```.env``` directory. similar to ```node_modules``` except this is considered an environment definition (the ```create``` flag) so it has a version of python installed and other concerns, as well. you can also execute a ```conda install <PACKAGE>```  to install whatever you need to add a la ```npm i```; [rtfm](https://docs.conda.io/projects/conda/en/4.6.1/user-guide/tasks/manage-environments.html)
  * you still need to activate the environment we just created:
    * ```conda activate <ENVNAME>```
    * you can always turn the environment off with ```conda deactivate```
  * launch Jupyter server with ```jupyter notebook```
* Sharing project
  * can either share entire directory - inefficient because of large files
  * use a YAML file
    * to create a YAML file for a project:
      * ```conda env export --prefix ./env > environment.yml```
    * to create a new environment named ```env_from_file```  from an existing YAML file named ```environnment.yml```:
      * ```conda env create --file environment.yml --name env_from_file```



