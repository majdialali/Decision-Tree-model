
Overview:

A decision tree model is implemented on a medical data set to guess if a person will get whether or not a patient will have diabetes within 5 years.


About data set:

The dataset describes the medical records for Pima Indians and whether or not each patient will have an onset of diabetes within five years. It is relatively small where it has 8 features and 768 rows. The link is here: https://www.kaggle.com/kumargh/pimaindiansdiabetescsv


Model selection and building:

We choose to use decision tree to train the data set using Scikit-learn library.

Decision tree model might not be the best model for this data set but we choose We choose to use it for training’s seek.

We have found  four approaches for building the tree:

1) traditional data splitting:
Via Scikit-learn's model selection, 
After reading the cvs-file, we divided the data set into three parts, implemented the model on the data, finding the accuracy, and plotting the confusion table and the decision tree.
By looking at the tree and dividing the data set randomly, we observe the overfitting problem. 
2) post pruning (ccp-alphas):
First, we made a comparison between accuracy of train and test sets given different alphas to decide the best alpha for this specific data set. Then we followed the same steps as the previous approach. This advantage of this approach is reducing the branches of the tree. Consequently, the tree is more readable, and less overfitted. 
3) cross validation with pruning:
This approach builds on the previous one and add a new dimension to it which is cross validation. The plotted tree looks very good. It has least branches. But it is clearly observed that the accuracy score is less previous one. Consequently, there is a change for underfitting.

4) stratified k-folds cross validation:
It builds on the last two approaches with some major improvements. 
Because the data set has unbalanced classes, we had to use stratified k-folds cross validation, not just the traditional cross validation. We choose 5 folds because of data set is small. The magical thing we did to reach an optimized classifier, is that we found the best fold and best ccp-alpha for this specific data set. In other words, we test every single alpha with every single fold, and measure the accuracy for them all. Then we choose the best fold and alpha by highest accuracy. We want to pay your attention that we had to keep truck on all the details to reach a somehow optimal model. However, there are two downsides of this approach. The first one is that the tree is relatively big compared with the tree of the previous approach, and the second one is that this approach can be computationally expensive with large data sets. But anyway it still a very good approach where overfitting and underfitting are avoided, and in the same time it gives a high accuracy score of the predictions.


