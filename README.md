# A Deep Learning Prediction Model for On-Site Earthquake Early Warning in India

![image](https://github.com/PavanMohanN/EEW_system_Variational/assets/65588614/7673bf77-604a-4b8a-9bcd-53fada23d96c)

## Overview

This repository contains code for an earthquake early warning system based on a conditional variational autoencoder (VAE). The system is designed to predict 27 spectral accelerations using 8 input variables: Peak Ground Acceleration ($PGA$), Peak Ground Displacement ($PGD$), Predominant Frequency ($F_p$), 5-95% Significant Duration  ($T_{sig}$), Arias Intensity ($I_a$), Cumulative Absolute Velocity  ($CAV$), Site Class ($S_c$), and direction flag ($dir$).

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
