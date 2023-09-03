# 🎯 Project Brief

Final ranking position will be awarded based upon:
* the smallest test set
* highest accuracy rate in part 1
* highest accuracy rate in part 2

### The Problem

The aim of this project is to accurately predict which multiple choice answers a student will choose given different forms of comprehension problems.


**Project Objective**

The model's output (predicting a student's response) involves 2 parts:
- predicting whether the student will get an answer right or wrong, and 
- predicting the exact option the student will choose in a test.

Solving for the first part is very important in determining the answer to the second part. 

### Frame The Problem
The problem is a supervised learning problem. The values to be predicted (`pass` / `fail` or `A, B, C, D`) and selected value are contained or derivable from the dataset.

The problem is a binary and multi-class classification, since our model prediction options are Yes/No and one of 4 multiple choice options. 

The project will use batch learning of already collected data: the 11,402 student response data points.

### Select a Performance Measure

We'll be testing our model's performance using accuracy. We'll use cross-validation to evaluate our model.

### The Data
There are 11,402 student response data points.

* **Mock Exams (folder)**
    * Questions: this is a folder that contains all the original comprehension passages and questions
    * Text: this is a folder that contains any additional comprehension passages that are not found in the Questions folder
    * Mock Exam Data (Labelled).xlsx: this is a spreadsheet containing all the student responses for the mock exams. Each tab is for each mock exam, the passage type is highlighted in yellow in A1, there is a column for the question type, the question number, the answer, and each student's response with the time in which they completed it.
* **Worksheets (folder)**
    * Questions: this is a folder that contains all the original comprehension passages and questions
    * worksheet data.xlsx: this is a spreadsheet containing all the student responses for the mock exams. It is structured similarly to the Mock Exam Data (Labelled) spreadsheet.
* question key: this is a spreadsheet defining the question types.
* student profiles: this is a spreadsheet containing the student's ID number and their birthday.

### Data Cleaning
There is a substantial amount of data that needs to be organised. Each piece of work includes its original passage, questions to the passage, multiple-choice options for each, student response data and student data. Each text has metrics which need to be computed. 

The final dataframe should the following fields:
- Indexes: id, date of birth, age at completion (year, month, day), time of completion, text, genre
- questions
- question type
- literary skills (vocabulary skills, punctuation skills, knowledge of idioms)
- application of skills (factual recall, inference, SPaG (spelling, punctuation and grammar), vocabulary, purpose)
- question difficulty (Difficulty Index and Discrimination Index)
- text metrics (flesch, flesch-kincaid, ari, gunning_fog, coleman-liau, linsear write, spache, smog and dale schall scores)
- student response
- correct answer
- pass / fail
- genre score: an ordered category where genre is scored by difficulty
- difficulty index: calculated by computing the total of students who got question correct divided by the total students
- discrimination index: high-scoring half who correctly answered (hc) minus low-scoring half who answered correctly (lc) divided by half of total students

### Visualizing The Data

**Spread of Students' Skills**

Vocabulary, grammar and purpose indexes have bimodal distributions. True-False index is right skewed, and factual recall and inference indexes are tri-modal distributions.
The following features are correlated with the `Passed` variable:
*total_score
* vocabulary_index
* true_false_index
* factual_recall_index
* inference_index
* purpose_index
* comprehensive_ability_index
* difficulty_index
* point_biserial_corr

### Machine Learning
The best model & parameter combinations are the Logistic Regression, Linear SVC, Gradient Boosting Classifier and MLPClassifier models with the 2nd degree polynomial variables 

### Final Solution
The final model is the Gradient Boosting Classifier with 2nd degree polynomial parameters:
* Passed Accuracy = 73%
* Student Response Accuracy (without passed variable) = 27%
* Student Response Accuracy (with passed varaible) = 
