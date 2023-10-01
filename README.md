# EEG-Based Biometric Authentication System

##Intro
EEG-Based Biometric Authentication System is an innovative project developed by the Queen's Cerebral Language and Innovation Team. Some project details and findings below, for more insights on the project [Download the research paper (PDF)](EEG_based_authentication_using_binary_cl.pdf). [Visit our team's website here.](https://www.queenscli.team/)


## Overview

In this project, we have developed an EEG-based biometric authentication system using machine learning techniques. The system utilizes motor movements as a means of authenticating users by analyzing their brainwave patterns. The EEG BCI dataset, consisting of recordings from 109 subjects performing various motor movements and motor imagery tasks, was used to train and test the authentication algorithm.

## Methods

### System Overview

Our system begins by organizing four raw EEG recordings of a specific user performing various motor movements into an array. The first and last two recordings are concatenated to form a motor movement pair. This preprocessing step speeds up subsequent processing while preserving the uniqueness of the motor movement data. Independent Component Analysis (ICA) is then applied to identify the independent brain patterns associated with each motor movement. A binary feed-forward neural network uses this processed data to train and authenticate users.
<img width="904" alt="Pipeline" src="https://github.com/mbenhamu/EEG-UserIdentification/assets/79335280/05f863a4-88d4-4e03-a924-074e099af437">

### Data Preprocessing

We use the MNE Python package to preprocess the raw EEG data. The frequency range is filtered to include 14 to 30 Hz, focusing on the beta wave range. Fast ICA is employed to separate the signal into subcomponents, resulting in a 64 by 15 array of post-processed data, representing different groupings of electrode sensors that describe the motor movements.


<img width="856" alt="ICA" src="https://github.com/mbenhamu/EEG-UserIdentification/assets/79335280/8eb5faae-d526-4432-bf9b-40db3f17d98b">

### Resampling
To increase the training data, we simulate new data by sampling from the original dataset. Synthetic Minority Over Sampling Technique (SMOTE) is used to generate more data, ensuring that the authentic user's data is well-represented.

### User Authentication Network

The user authentication algorithm employs a binary classification neural network. The network takes a 64 by 45 array representing concatenated motor movements, flattens it, and passes it through input and hidden layers. Dropout layers are used for regularization. After training, if the network outputs a 1, the user is authenticated.


## Results 

### Training Data

The network achieved an accuracy of 99.5% on the training data, with a loss of 0.0168 after 30 epochs.

### Testing Results

On the validation data, the network achieved an accuracy of 100% with a low loss.



