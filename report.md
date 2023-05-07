## Overview of the Analysis

The purpose of the following analysis was to use a large data set of applicants looking for funding and try to predict which applicants would eventually become successful. The CSV contained more than 34,000 organizations that had recieved funding from Alphabet Soup over the years. Contained within this dataset was information for company identifiction(EIN and Name), the Alphabet Soup application type, the affiliated sector of industry, the government organization classification, the use case for funding, the organization type, the active status, the income classification, the special considerations for application, the funding amount requested, and was the money used affectively (was it successful).

In order to complete the analysis with neural networks, 3 process needed to be completed. First, the preprocessing of the data, next the training, and lastly the building of the model(and evaluation). For the preprocessing, I removed columns, binned certain data to reduce the noise, and then scaled the data using StandardScaler to ensure that larger values would not cause any bias.

Once I completed this process, I seperated out the variables from the result I was trying to predict, then I split the data into a training and testing segment. Afterwards, I used tensorflow/keras to create the model, neural network. Lastly, the model was evaluated for its accuracy on the testing data.


## Results

The target for our model was the 'IS_SUCCESSFUL' field while all other columns were features, not including 'EIN' and 'NAME' which we removed due to them not being targets or features.

* Neural Network Model 1:
  * In this model 2 hidden layers and 1 output layer was used. The layers in chronological order had 80,30,1 neurons.
  * The standard activation model of 'relu' was used for the first two layers and 'sigmoid' was used for the output layer due to it needing to be either true or false.
  * Model 1 has about .725 accuracy, which is still fairly good but below the 75% target.
  
* Neural Network Model 2,3,4:
  * In the final iteration, model 4, we removed the 'status' and 'special considerations' to see if we could further improve accuracy and we did indeed have a small improvement.
  * While we did some changes in the binning of 'classification' and 'application_type', they did not improve the model so they were not used.
  * We ended up with 3 hidden layers and 1 output layer. The layers in chronological order had 60,25,10,1 neurons.
  * In the preceding models, we had slow improvement as we tried to optimize, but this is a short list of some of the changes that were attempted: more hidden layers, more columns removed, different bin sizes, different number of neurons, changing epochs.
  * In model 4 we had an accuracy of .731 which was the highest of all the models but unfortunately still below our .75 target.

## Summary

When looking at the results from our models we can conclude that our final model was superior to all preceding models although it was still below our target of 75% accuracy. That being said, the final model was able to predict whether an applicant would be successful 73% of the time based on the data we recieved.

It is worthy of note that there are other different types of models which could work better in this instance due to the classification issue. One such model that I would recommend would be Decision trees. Decision trees are often used for classification problems and are better than neural networks at handling non-linear relationships. An extension of this that could also be useful are random forests which are able to combine the predictions of the multiple trees that are made.

