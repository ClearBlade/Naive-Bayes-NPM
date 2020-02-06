# Naive-Bayes Classifier

## Contents

### [Overview](#overview-1)
### [System Installation](#system-installation)
### [Steps for Transpilation to ES5](#transpilation-to-es5)
### [Usage](#usage-1)
### [Assets](#assets-1)

## Overview

A naive bayes classifier can be implemented using this library to run on the ClearBlade Platform for classification purposes. This library can be used to implement two types of naive bayes algorithms - **Gaussian Naive Bayes** and **Multinomial Naive Bayes**. 

The **Gaussian Naive Bayes** algorithm is typically used when the features follow a normal distribution i.e the training data has features that are *continuous*. The **Multinomial Naive Bayes** algorithm is used when the features are *discrete*.

[Difference between discrete and continuous features](https://hackernoon.com/continuous-vs-discrete-variables-in-the-context-of-machine-learning-15d9005e2525)

This is an ipm package, which contains one or more reusable assets within the ipm Community. The 'package.json' in this repo is a ipm spec's package.json, [here](https://docs.clearblade.com/v/3/6-ipm/spec), which is a superset of npm's package.json spec, [here](https://docs.npmjs.com/files/package.json).

[Browse ipm Packages](https://ipm.clearblade.com)

## System Installation

1. Open the ClearBlade Platform and enter your login credentials
```
https://platform.clearblade.com/
```
2. Click on **Add System** -> **Advanced** and copy the link of this repository in the box.
```
https://github.com/ClearBlade/brain-js
```
3. Click **Create**
4. You can now access this system in the platform.

## Transpilation to ES5

Follow these [steps](https://github.com/ClearBlade/Machine-Learning-Node-Libraries/blob/master/README.md#steps-for-transpilation-to-es5-1) for transpilation of any NPM package to ES5 so that the NPM package can be imported as a library in the clearblade code engine.

## Usage

- This IPM package consists of a Naive Bayes Library that can be imported in the ClearBlade Platform in order to train and test machine learning models on the platform.

- The API Documentation for this library can be found [here](https://mljs.github.io/naive-bayes/).

- [A simple example of how the naive bayes classifier does the prediction task](https://www.geeksforgeeks.org/naive-bayes-classifiers/)

- Before defining the classifer, we first define the training data. This data includes Readings recorded from 3 sensors (Power, Temperature and Accelerometer) inside a machine. The training labels are also defined which give information about whether a maintenance was required for a given set of sensor values. ( 0 - Maintenance Not Required; 1 - Maintenance Required )

``` javascript
   var inputs = [
    [1350, 73.4, 0.0683], 
    [1350, 73.4, 0.0685], 
    [1532, 83.1, 0.5272], 
    [1710, 77.3, 1.7210], 
    [1200, 76.6, 0.0688], 
    [1820, 82.1, 0.4333], 
    [1421, 75.4, 0.0695], 
    [1800, 95.1, 1.9000], 
    [1520, 82.4, 0.4272], 
    [1740, 95.0, 1.7150]
  ]; 
  
  var outputs = [0, 0, 0, 1, 0, 1, 0, 1, 0, 1]; 

```

- After defining the data, load the Naive Bayes library. The following snippet loads the library and allows your code to access functionality of the library APIs via the **model** variable. The algorithm used in this example is Gaussian Algorithm.

``` javascript
  var gaussian = NaiveBayes().GaussianNB;
  var model = new gaussian();
```

- Once we define the **model** variable, we train the model with the given input and output data.

``` javascript
  model.train(inputs, outputs); 
```

- Once the classifer is trained, predict for a given set of sensor values, if a maintenance is required or not.

``` javascript
   var test = [[1780, 95.5, 1.8120]];
   var prediction = model.predict(test)
```

- Multinomial Naive Bayes can also be implememted as shown below.

``` javascript
   var multinomial = NaiveBayes().MultinomialNB;
   var model = new multinomial();
   model.train(inputs, outputs); 
  
   // Predict if maintenance is required for sensor values - { power: 1780, temperature: 95.5, accelerometer: 1.8120 }
   var test = [[1780, 95.5, 1.8120]];
   var prediction = model.predict(test)
```

- The implementation of this library is done in the [smoke test](https://github.com/ClearBlade/naive-bayes/blob/master/code/services/NaiveBayesSmokeTest/NaiveBayesSmokeTest.js) and you can refer to the [**Official Documentation**](https://github.com/mljs/naive-bayes) of that library to explore more options that you can use.  

## Assets

### Libraries 

| Library  | Description  | Official Documentation |   
|---|---|---|
| ``` NaiveBayesLibrary ```  | A Library Implementing Gaussian and Multoinomial Naive Bayes Algorithms | https://github.com/mljs/naive-bayes  | 

### Code Services

``` NaiveBayesSmokeTest ``` : A code service to show working of Naive Bayes Library.

