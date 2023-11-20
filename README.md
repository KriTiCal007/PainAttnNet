## Transformer Encoder with Multiscale Deep Learning for Pain Classification Using Physiological Signals

## Directory Structure
```python
PainAttnNet
|   environment.yml # Requirements for conda environment
|   LICENSE
|   README.md
|   requirments.txt # Requirements for pip environment
|          
+---jq
|       jq-win64.exe
|       
\---src
    |   batch_train.sh # Training script
    |   config.json # Training configurations
    |   logger_config.json # Logger configurations
    |   parser.py # Parser for training configurations
    |   train_kfold_cv.py # Main training script
    |  __init__.py
    |   
    +---models
    |   |   main_painAttnNet.py # Main model wrapper
    |   |   module_mscn.py* # Multiscale convolutional network
    |   |   module_se_resnet.py # Squeeze-and-excitation residual network
    |   |   module_transformer_encoder.py # Transformer encoder block
    |   \   __init__.py
    |           
    +---tests # Unit tests
    |   |   test_generate_kfolds_index.py
    |   |   test_mscn.py
    |   |   test_PainAttnNet_output.py
    |   |   test_process_bioVid.py
    |   |   test_se_resnet.py
    |   |   test_transformer_encoder.py
    |   \   __init__.py
    |           
    +---trainers # Training modules
    |   |   checkpoint_handler.py # Checkpoint handler
    |   |   device_prep.py # Device preparation, CPU or GPU
    |   |   main_trainer.py # Main trainer scripts
    |   |   metrics_manager.py # Metrics manager and other metrics functions
    |   \   __init__.py
    |           
    \---utils
        |   process_bioVid.py # Data processing for BioVid
        |   utils.py # Other utility functions
        \   __init__.py

```  
## Get Started

```
torchaudio==0.13.0
python==3.10.8
pytorch-cuda==11.7
pytorch==1.13.0
torchvision==0.14.0
scikit-learn==1.0.1
pandas
matplotlib
openpyxl
```
For Linux users, install `jq` package via conda or pip.

For Windows users, install `jq` package from [here](https://stedolan.github.io/jq/download/), and put the `jq.exe` file in the local directory.


## Training


### Training k-fold cross validation with script
```
sh batch_train.sh
```
### Training individual fold in terminal
```
python train_kfold_cv.py --fold_i {fold index}
```

You can change settings at `main_painAttnNet.py` for tuning model structure, `config.py` for training configurations and `train_kfold_cv.py` for others.


## Dataset
The dataset is available at [BioVid Heat Pain Database](https://www.nit.ovgu.de/BioVid.html).

