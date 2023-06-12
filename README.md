# Track 2: Forecasting Future Turn-Based Strokes in Badminton Rallies

## :badminton: Task Introduction
The goal of this track is to **forecast future strokes including shot types and locations given the past stroke sequences**, namely stroke forecasting. For each singles rally, given the observed 4 strokes with type-area pairs and two players, the goal is to predict the future strokes including shot types and area coordinates for the next n steps. n is various based on the length of the rally.

## :badminton:	prerequisite
* Coding environment: VS Code 
* Packages version: python 3.11 

## Usage
#### Train a model
```=bash
./script.sh
```
#### Generate predictions
```=bash
python generator.py {model_path}
```
#### Run evaluation metrics
- Both ground truth and prediction files are default in the `data` folder
```=bash
python evaluation.py
```

## :badminton:	Hyperparameters 
* seed_value: 42

* max_ball_round: 70

* encode_length: 4

* batch_size: 16

* lr: 1e-4

* epochs: 150

* shot_dim: 256

* area_num: 5

* area_dim: 256

* player_dim: 256

* encode_dim: 256

## :badminton:	Experiment Results
training loss: ![image](https://github.com/derricko722/AI-Final-Project/blob/main/loss.png)
prediction: https://github.com/derricko722/AI-Final-Project/blob/main/prediction.csv
