#Fashion Forward: Forecasting Visual Style in Fashion
Ziad Al-Halah, Rainer Stiefelhagen, Kristen Grauman
[Paper Link](https://arxiv.org/abs/1705.06394)

#### Goal
The paper introduces a novel problem of forecasting future fashion trends. 

#### Challenges and Novelty
* Novel and interesting problem, not addressed yet
* Uses unlabelled data

#### Dataset
Amazon purchase data for 3 categories: shirts, dresses and tops/tees from January 2008 to December 2013

#### Proposed Solution

* Learning Latent Style from images:
	Learn attribute representation of unlabelled images using a pretrained model of DeepFashion. There are 1000 attribute values
	Perform non-negative matrix factorization on the attribute distribution to learn high level style for each image. The factorization is done to generate 30 styles.
	Each style is represented using a combination of attributes, analogous to learning word distribution for latent topics
	Each image is a weighted mixture of these styles, analogues to topic distribution for a document.
* Forecasting Style:
	We define time-steps as an interval, which is a month in this case
	For every transaction, gather the images of products  solf
	For every style, compute the temporal trajectory of the style using the images of the transactions in every time-step. 
	Given the trajectory of the style upto time n, predict the trajectory for time n+1 using exponential smoothening. 

#### Experiments

* Baselines for forecasting:
	Naive:
	1) mean: it forecasts the future values to be equal to the mean of the observed series; 
	2) last: it assumes the forecast to be equal to the last observed value; 
	3) drift: it considers the general trend of the series.
	
	Regression: Lag based regressors:
	1) linear autoregression model (AR); 
	2) the autoregression model that accounts for seasonality (AR+S); 
	3) the vector autoregression (VAR) that considers the correlations between the different styles’ trajectories;
	4) and the autoregressive integrated moving average

	Neural Networks:
	1) The feed forward neural network (FFNN); 
	2) and the time lagged neural network (TLNN) model (ARIMA).

* Baselines for fashion representation:
	* Tag based
	* Text
	* Visual Alexnet FC7
	* Visual Alexnet M3
	* Attributes+ Tags
	* Attributes + Text
	* Attributes + Tags+ + Text

* Experiment for categorising styles as out-of-fashion, re-emerging and so on.
* Experiment for forecasting attributes popularity for the popularity of a style


#### Conclusion/Limitation

First attempt at the problem statement
Interesting problem for fashion industry

Intuition behind the architecture is unclear
Attributes are limited to 1000 attributes of deep fashion dataset. 
It is unclear how many of these attributes are color based, pattern based and so on.
What is the attribute level performance of the model for unseen unlabelled images. How much error is propagated to fashion forecast

