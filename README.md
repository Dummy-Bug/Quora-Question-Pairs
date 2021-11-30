<h1 style="text-align:center;font-size:30px;" > Quora Question Pairs </h1>
<h1> 1. Business Problem </h1>

<p>Quora is a place to gain and share knowledge—about anything. It’s a platform to ask questions and connect with people who contribute unique insights and quality answers. This empowers people to learn from each other and to better understand the world.</p>
<p>
Over 100 million people visit Quora every month, so it's no surprise that many people ask similarly worded questions. Multiple questions with the same intent can cause seekers to spend more time finding the best answer to their question, and make writers feel they need to answer multiple versions of the same question. Quora values canonical questions because they provide a better experience to active seekers and writers, and offer more value to both of these groups in the long term.
</p>
<br>
         *** Credits: Kaggle ***
<br>
<p> </p>
<h4> Problem Statement </h4>

- Identify which questions asked on Quora are duplicates of questions that have already been asked. 

- This could be useful to instantly provide answers to questions that have already been answered. 

- We are tasked with predicting whether a pair of questions are duplicates or not. 

<h2> 1.2 Sources/Useful Links</h2>

- Source : https://www.kaggle.com/c/quora-question-pairs
<br><br>____ Useful Links ____
- Discussions : https://www.kaggle.com/anokas/data-analysis-xgboost-starter-0-35460-lb/comments
- Kaggle Winning Solution and other approaches: https://www.dropbox.com/sh/93968nfnrzh8bp5/AACZdtsApc1QSTQc7X0H3QZ5a?dl=0
- Blog 1 : https://engineering.quora.com/Semantic-Question-Matching-with-Deep-Learning
- Blog 2 : https://towardsdatascience.com/identifying-duplicate-questions-on-quora-top-12-on-kaggle-4c1cf93f1c30

<h2>1.3 Real world/Business Objectives and Constraints </h2>

1. The cost of a mis-classification can be very high. Imagine a scenario if we declare two questions to be duplicate but they are not duplicate , then all the answers that were referred to question1 will be referred to question2 which can be extremely dangerous. 

2. You would want a probability of a pair of questions to be duplicates so that you can choose any threshold of choice.because if we predict only 1 or 0 then it would not tell us how confident we are with our prediction , but since we want misclassification to be very very less 


3. No strict latency concerns.even if it takes quora to identify that questions are duplicate  a couple of seconds it would not matter much.

4. Interpretability is partially important.

<h1>2. Machine Learning Probelm </h1>

<h2> 2.1 Data </h2>

<h3> 2.1.1 Data Overview </h3>
<p> 
- Data will be in a file Train.csv <br>
- Train.csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate <br>
- Size of Train.csv - 60MB <br>
- Number of rows in Train.csv = 404,290

</p>

<h3> 2.1.2 Example Data point </h3>

<h2> 2.2 Mapping the real world problem to an ML problem </h2>

<h3> 2.2.1 Type of Machine Leaning Problem </h3>

<p> It is a binary classification problem, for a given pair of questions we need to predict if they are duplicate or not. </p>

Source: https://www.kaggle.com/c/quora-question-pairs#evaluation

Metric(s): 

* log-loss : https://www.kaggle.com/wiki/LogarithmicLoss ,it makes sense to use log-loss as performance metric as we don't want to just classify question pair to be 0 or 1 rather we also want the probability , and whenever we need the probability values log-loss is the best metric to use.

* Binary Confusion Matrix
This is our secondary matrix we will also use Binary Matrix to understand what is happening using it we can use precision , recall , tpr , fpr , tnr and fnr .
