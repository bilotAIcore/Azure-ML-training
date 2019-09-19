---
Date: "2019-09-18"
Step: 'Model tuning'
Description: Model train & optimisation exercise, using the Steel Plates data.
---
  
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRe28kRsvMfHCz-rQz5oZgtVJhks1S6_W5W0WRcudlJf3_WVS5J" width="150" style="float:right;"/>

# Model Optimisation
  
## 1. Import Data

Load saved Dataset for steel plates. <br />
This can be found under the *Saved Datasets* section in the operator menu.

## 2. Remove correlated features
<p>Drop features that are highly redundant. This can be 
done either manually, or programmatically.</p>

## 3. Split data
<p>Make sure the random sampling of data is representative. 
This can be achieved by doing stratified sampling, within 
the classes of the Label.</p>

## 4. Model optimisation
<p>This step requires two operators; a trainable model and
<b>Tune Model Hyperparameters</b>. Remember that the the tuning 
is to be done on the <i>training</i> data.</p>

- <b>Model</b>: train mode needs to be set to <i>Parameter Range</i>

- <b>Tuning</b>: here ione needs to configure the (1) sweeping mode, (2) number of runs, (3) the label, and (4) the metric for evaluating model performance.

<p>As this is a multi-class classification problem, 
the evaluation metrics that are easiest to interpret are 
Accuracy and Average Log Loss.</p>

## 4. Model evaluation
Finally, add these operators to get an idea how well the model(s) performs

- <b>Score model</b> operator

- <b>Evaluate model</b> operator

<p>In the <b>Evaluate model</b> operator, one can compare the
performance between two different models.</p>