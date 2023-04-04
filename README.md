# NeurIPS22:  CLEAR: Generative Counterfactual Explanations on Graphs

Code for the NeurIPS 2022 paper [*CLEAR: Generative Counterfactual Explanations
on Graphs*.](https://openreview.net/pdf?id=YR-s5leIvh).

<span style="color: cyan;">Lines in cyan were added by Armagaan.</span>

## Environment
```
Python 3.6
Pytorch 1.2.0
Scipy 1.3.1
Numpy 1.17.2
Torch-geometric 1.7.2
```

## Dataset
- Datasets can be found in [link](https://virginia.box.com/s/941v9pwh83lfw5vnwfbgcertlsoivg5j).
- <span style="color: cyan;">Create a directory named `dataset` in the repo's home directory.</span>
- <span style="color: cyan;">Store the pickled files here.</span>

## Run Experiment
### Step 1:  Training a graph prediction model
- <span style="color: cyan;">cuda device is hardcoded in `train_pred.py` (line 55), `models.py` (lines 10, 200), and `main.py` (line 65). Change according to your need.</span>
- <span style="color: cyan;">Create a directory named `models_save/prediction` in the repo's home directory.</span>
- Train a graph prediction model (i.e., the model which needs explanation). The trained prediction models used in this paper can be directly loaded from ```./model_save/```.
- If you want to train them from scratch, run the following command (here we use the dataset *imdb_m* as an example):
```
python train_pred.py  --dataset imdb_m --epochs 600 --lr 0.001
```
Or you can also use any other graph prediction models instead.

### Step 2: Generating counterfactual explanations
```
python main.py --dataset imdb_m --experiment_type train
```
Here, when ```experiment_type``` is set to *train* or *test*, the model CLEAR will be trained or loaded from a saved file. When it is set to *baseline*, you can run the random perturbation based baselines (INSERT, REMOVE, RANDOM) by setting ```baseline_type```.

### Refenrences
The code is the implementation of this paper:


[1] Jing Ma, Ruocheng Guo, Saumitra Mishra, Aidong Zhang, Jundong Li. CLEAR: Generative Counterfactual Explanations on Graphs. Neural Information Processing Systems (NeurIPS), 2022. 


