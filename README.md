# Learning Probability Density Functions Using Data Only

## Overview
This assignment focuses on learning an unknown probability density function (PDF) directly from data, without assuming any mathematical form of the distribution. A Generative Adversarial Network (GAN) is used to learn the distribution of a transformed random variable using only sample data.

The dataset used contains air quality measurements from Indian cities, and the NO₂ (nitrogen dioxide) concentration is chosen as the feature for this task.

---

## Objective
The main goals of this assignment are:
- To apply a non-linear transformation to real-world data
- To assume the transformed data comes from an unknown distribution
- To learn this unknown distribution using a GAN
- To approximate and visualize the learned probability density function

No parametric distribution such as Gaussian or exponential is assumed at any stage.

---

## Step 1: Transformation of the Data
Each NO₂ value (x) is transformed into a new variable (z) using the following function:

z = x + aᵣ sin(bᵣ x)

The parameters aᵣ and bᵣ depend on the university roll number r:
- aᵣ = 0.5 (r mod 7)
- bᵣ = 0.3 (r mod 5 + 1)

This transformation adds non-linearity to the data and ensures that each student works with a slightly different distribution.

---

## Step 2: Learning the Distribution Using GAN
Since the probability density function of the transformed variable z is unknown, a Generative Adversarial Network (GAN) is used to learn it.

- The **generator** takes random noise sampled from a standard normal distribution and generates fake samples.
- The **discriminator** tries to distinguish between real transformed samples and generated samples.

Through adversarial training, the generator learns to produce samples that follow the same distribution as the real data.

The GAN learns the distribution only from samples, without using any explicit PDF formula.

---

## Step 3: PDF Approximation
After training the GAN:
- A large number of samples are generated from the trained generator
- Kernel Density Estimation (KDE) is applied to these samples
- The KDE plot gives an approximation of the learned probability density function

---

## Results and Observations
- The GAN learns the overall shape of the transformed data distribution
- The main peaks in the generated PDF align well with the real data
- Training is mostly stable, with expected fluctuations in losses
- The learned PDF is smooth and non-parametric



