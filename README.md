# A Deep Learning Prediction Model for On-Site Earthquake Early Warning in India

![image](https://github.com/PavanMohanN/EEW_system_Variational/assets/65588614/7673bf77-604a-4b8a-9bcd-53fada23d96c)

## Overview

This repository contains code for an earthquake early warning system based on a conditional variational autoencoder (VAE). The system is designed to predict 27 spectral accelerations using 8 input variables: Peak Ground Acceleration ($PGA$), Peak Ground Displacement ($PGD$), Predominant Frequency ($F_p$), 5-95% Significant Duration  ($T_{sig}$), Arias Intensity ($I_a$), Cumulative Absolute Velocity  ($CAV$), Site Class ($S_c$), and direction flag ($dir$). 

## Library Installation and Importing Libraries

### Installation

Ensure you have Python 3.x installed. Use the following pip commands to install the necessary libraries:

<code>pip install numpy pandas matplotlib scikit-learn keras tensorflow</code><br>

<h3> Importing the libraries </h3>

<code>import numpy as np</code><br>
<code>import pandas as pd</code><br>
<code>import matplotlib.pyplot as plt</code><br>
<code>from sklearn.model_selection import train_test_split</code><br>
<code>from sklearn.preprocessing import MinMaxScaler, StandardScaler</code><br>
<code>from scipy.stats import kurtosis</code><br>
<code>from keras.layers import Input, Dense, Lambda</code><br>
<code>from keras.models import Model, Sequential, load_model</code><br>
<code>from keras import backend as K</code><br>
<code>from keras.losses import mse</code><br>
<code>from keras.optimizers import Adam</code><br>
<code>from keras.callbacks import ModelCheckpoint, Callback</code><br>
<code>import tensorflow as tf</code><br>

## About the libraries

- numpy: For numerical operations and array manipulations.
- pandas: For data manipulation and handling.
- matplotlib.pyplot: For plotting graphs and visualizations.
- sklearn.model_selection.train_test_split: For splitting data into training and testing sets.
- sklearn.preprocessing.MinMaxScaler, sklearn.preprocessing.StandardScaler: For scaling numerical input data.
- keras.layers: For defining layers in the neural network model.
- keras.models: For defining and manipulating the neural network models.
- keras.backend: Provides operations that are not yet part of the official Keras API.
- keras.losses.mse: Mean squared error loss function, commonly used in regression tasks.
- keras.optimizers.Adam: Optimizer algorithm for gradient-based optimization.
- tensorflow: Backend framework for Keras deep learning library.
- keras.callbacks.ModelCheckpoint: Callback to save the model after every epoch.
- keras.callbacks.Callback: Base class for Keras callbacks.

## Architecture

The core of the system is a VAE, which is trained to map spectral accelerations to themselves. The CVAE consists of:
- *Encoder*: Maps spectral accelerations to a latent space.
- *Decoder*: Reconstructs spectral accelerations from the latent space.

## Input Mapping Layers - The game changer
Given that spectral accelerations are not known beforehand in an early warning scenario, additional layers are designed to map the input variables directly to the latent space of the VAE. This architecture involves:
- *Two separate layers*: These map the 8 input variables ($PGA, PGD, F_p, T_{sig}, {I_a}, CAV, S_c, dir$) to the latent space of the VAE.
- *Concatenation*: The encoder component of the VAE is disconnected, and the layers mapping inputs to the latent space are concatenated directly.

## Output

This architecture facilitates a direct mapping from the input variables to the predicted spectral accelerations, enabling real-time earthquake early warning predictions.
