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
*seed_value: 42

*max_ball_round: 70

*encode_length: 4

*batch_size: 16

*lr: 1e-4

*epochs: 150

*shot_dim: 256

*area_num: 5

*area_dim: 256

*player_dim: 256

*encode_dim: 256


## :badminton:	Evaluation Metrics

$$ 
\begin{flalign}
&Score = min(l_1, l_2, ..., l_6)&
\end{flalign}
$$

$$ 
\begin{flalign}
l_i = AVG(CE + MAE)&
= \frac{ \sum_{r=1}^{|R|} \sum_{n=\tau+1}^{|r|} [S_n log \hat{S_n} + (|x_n-\hat{x_n}|+|y_n-\hat{y_n}|)]} {|R|\cdot(|r|-\tau)} &
\end{flalign}
$$


## :badminton:	Baseline: ShuttleNet
### Overview
ShuttleNet is the first turn-based sequence forecasting model containing two encoder-decoder modified Transformer as extractors, and a position-aware gated fusion network for fusing these contexts to tackle stroke forecasting in badminton.
Please refer to the [paper](https://ojs.aaai.org/index.php/AAAI/article/view/20341) for more details.
Here we adapt ShuttleNet to our newly collected dataset as the official baseline in the CoachAI Badminton Challenge.
All hyper-parameters are set as the same in the paper.

### Code Usage
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
