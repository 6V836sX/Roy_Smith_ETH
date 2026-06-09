---
markmap:
  colorFreezeLevel: 2
  maxWidth: 320
---

# ENEL445 Roy Smith Optimisation Block

## How to Use

### Best VS Code viewer

#### Install extension

##### Markdown Preview Markmap Support

##### Or Markmap / Markmap for VS Code

#### Open this file

##### Use Markdown Preview

##### The heading hierarchy becomes the mind map

### Why this file exists

#### Mermaid mindmap may not render in VS Code without extra Mermaid support

#### Markmap uses normal Markdown headings

#### The same file can be edited as plain text

#### The same structure can be imported into Xmind as Markdown

## Big Picture

### Engineering problem

#### noisy data

#### system model

#### constraints

#### prediction and control

### Mathematical model

#### variables

#### objective function

#### constraints

#### residuals or dynamics

### Optimisation structure

#### least squares

#### convex optimisation

#### LMI / SDP

#### MPC

### Exam use

#### formulate

#### classify

#### derive

#### explain assumptions

#### avoid common mistakes

## Least Squares

### Data fitting

#### What it is

##### Estimate parameters in y = Phi theta + epsilon

#### Why it matters

##### Simplest bridge from data to optimisation

#### Exam use

##### Build Phi, theta, y

##### Write min \|\|y - Phi theta\|\|\_2\^2

##### Derive normal equations

#### Memory hook

##### residual vector should be as short as possible

### Normal equations

#### Formula

##### Phi\^T Phi theta = Phi\^T y

#### Closed form

##### theta_hat = (Phi\^T Phi)\^(-1) Phi\^T y

#### Condition

##### Phi must have full column rank for inverse form

#### Common mistake

##### using Phi Phi\^T instead of Phi\^T Phi

### Geometric view

#### Projection

##### y is projected onto column space of Phi

#### Residual

##### residual is orthogonal to column space

#### Formula

##### Phi\^T(y - Phi theta_hat) = 0

## Nonlinear Least Squares

### Gauss and Ceres

#### Engineering problem

##### estimate orbit from limited observations

#### Model

##### y_obs = H(theta, t) + epsilon

#### Key idea

##### nonlinear model is solved by repeated local linear LS steps

### Linearisation

#### Start

##### theta_i

#### Approximate

##### H(theta) approx H(theta_i) + H_theta(theta - theta_i)

#### Solve

##### min \|\|delta y - H_theta delta theta\|\|\_2\^2

#### Update

##### theta\_{i+1} = theta_i + delta theta

### Exam use

#### Explain iterative refinement

#### Write the local LS update

#### Do not claim one linearised step is globally exact

## Statistics of LS

### Estimate as random variable

#### Because data contains random noise

#### theta_hat has bias and variance

### Bias

#### E\[theta_hat\] - theta_0

#### Unbiased means expected estimate equals true parameter

### Variance

#### spread of estimator around its mean

#### covariance matrix for vector estimates

### MSE

#### MSE = bias\^2 + variance

#### Minimum variance unbiased is not necessarily minimum MSE

### BLUE

#### Meaning

##### Best Linear Unbiased Estimator

#### Formula with covariance R

##### theta_hat = (Phi\^T R\^{-1} Phi)\^(-1) Phi\^T R\^{-1} y

#### Covariance

##### (Phi\^T R\^{-1} Phi)\^(-1)

#### Common mistake

##### assuming R = I when correlated noise is given

## Regularisation

### Motivation

#### reduce variance

#### improve conditioning

#### improve prediction

#### accept some bias

### Ridge / Tikhonov

#### Problem

##### min \|\|y - Phi theta\|\|\_2\^2 + eta \|\|theta\|\|\_2\^2

#### Solution

##### theta_hat = (Phi\^T Phi + eta I)\^(-1) Phi\^T y

### Bias-variance tradeoff

#### eta small

##### low bias

##### high variance

#### eta large

##### higher bias

##### lower variance

### Validation

#### split data

##### fitting set

##### validation set

#### choose eta by validation error

#### do not tune on training residual only

## Convex Optimisation

### Convex set

#### Definition

##### line segment between any two points stays inside

#### Formula

##### gamma x1 + (1-gamma)x2 in C

### Important sets

#### hyperplane

##### a\^T x = b

#### halfspace

##### a\^T x \<= b

#### norm ball

##### \|\|x - x_c\|\| \<= r

#### cone

##### gamma x in C for gamma \>= 0

#### PSD cone

##### X \>= 0

##### z\^T X z \>= 0 for all z

#### ellipsoid

##### (x-x_c)\^T P\^{-1}(x-x_c) \<= 1

### Convex problem

#### Convex objective

#### Convex inequality constraints

#### Affine equality constraints

#### Local information is globally useful

## Problem Classes

### LP

#### Linear cost

#### Linear constraints

#### Polytopic feasible region

#### Examples

##### diet

##### logistics

##### Chebyshev centre

### QP

#### Quadratic cost

#### Linear constraints

#### Examples

##### constrained least squares

##### portfolio optimisation

##### simple MPC

### SOCP

#### Norm cone constraints

#### \|\|Ax+b\|\|\_2 \<= c\^T x + d

#### QP can often be reformulated as SOCP

### QCQP

#### Quadratic objective

#### Quadratic constraints

#### Ellipsoid intersection intuition

### SDP / LMI

#### PSD matrix constraints

#### affine matrix expression

#### F(x) \>= 0

## LMI and Control

### LMI

#### Linear Matrix Inequality

#### F0 + x1 F1 + ... + xn Fn \>= 0

#### Constraint over PSD cone

### Schur complement

#### Converts block matrix positivity into equivalent inequality

#### Requires definiteness condition on block

### Stability

#### Continuous time

##### A\^T P + P A \< 0

#### Discrete time

##### A\^T P A - P \< 0

### State feedback

#### u_k = K x_k

#### closed-loop A + BK

#### variable substitution can make design convex

## Model Predictive Control

### Core loop

#### estimate current state

#### optimise future trajectory

#### apply first input

#### remeasure and replan

### Finite horizon cost

#### state penalty

##### x\^T Q x

#### input penalty

##### u\^T R u

#### terminal penalty

##### x_M\^T Q_terminal x_M

### Dynamics constraint

#### x\_{k+1} = A x_k + B u_k + F w_k

#### dynamics are constraints, not optional description

### Constraints

#### hard constraints

##### actuator limits

##### safety limits

#### soft constraints

##### comfort or target penalties

#### terminal constraints

##### recursive feasibility

##### stability

### Explicit MPC

#### solve parametric optimisation offline

#### state space split into polytopic regions

#### fast online

#### regions can grow exponentially

## Exam Priority

### Must know

#### LS formulation

#### normal equations

#### bias variance MSE

#### BLUE

#### regularisation

#### convexity definition

#### problem class identification

#### MPC formulation

### Should know

#### nonlinear LS linearisation

#### ellipsoid method idea

#### Schur complement

#### stability LMI

#### explicit MPC concept

### Recognise only

#### S-procedure details

#### deep CVX/YALMIP implementation

## Common Mistakes

### Least squares

#### wrong matrix dimensions

#### using inverse without rank condition

#### confusing residual error with errors in x and y

### Statistics

#### saying unbiased means minimum MSE

#### ignoring covariance R

#### using validation data for fitting

### Convex optimisation

#### checking only one line segment

#### treating nonlinear equality as convex

#### confusing positive definite and semidefinite

### LMI

#### applying Schur complement without checking block condition

#### not recognising matrix-valued constraints

### MPC

#### forgetting only first input is applied

#### forgetting dynamics are constraints

#### confusing feedforward forecast with feedback
