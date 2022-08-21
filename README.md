# RASA Core+NLU English and Other language
Chat Bot Natural Language Understanding and Processing for Indian local and International English Language

## System Requirement
1. Ubuntu 16+
2. Mac OS Latest
3. Windows 10 (Visual C++ Build tool)

## Install Mini Conda (Part of Anaconda)
https://conda.io/miniconda.html


## Install Python
Install Python using Conda. Rasa best works on Python 3.6
```
conda install python=3.6
```


## Create Environment for Rasa Project under Python 3.6
We except you have install python 3.6 using Conda command
```
conda create -n rasa python=3.6
```

## Install Visual studio Code and Open a Empty Folder
https://code.visualstudio.com/download

## Activate python 3.6 using Conda (important step)
```
source activate rasa
```

## Install Required Python Packages
Install Rasa NLU, Tensorflow, Spacy, Spacy ENG lang and Rasa Core
```
pip install  --no-cache-dir rasa_nlu
pip install  --no-cache-dir rasa_nlu[spacy]
python -m spacy download en_core_web_md
python -m spacy link en_core_web_md en
pip install  --no-cache-dir rasa_nlu[tensorflow]
pip install -U rasa_core==0.11.11
```

## Clone this repo
```
git@github.com:bikashkumars/rasa_core_nlu_oriya.git
```

## Run Rasa command to create Model
```
python -m rasa_nlu.train -c nlu_config.yml --data nlu.md -o models --fixed_model_name nlu --project current --verbose
```

## Test
```
python index.py
```

## Run as Server
```
python -m rasa_nlu.server --path projects
```

# Information
So far, you have suceefully completed RASA NLU. Now we will move to Rasa Core


## Train Rasa Core using Story and Domain
```
python -m rasa_core.train -d domain.yml -s stories.md -o models/dialogue
```

## Run rasa Code as Server
```
python -m rasa_core.run -d models/dialogue -u models/current/nlu
```

## Versions
pip show rasa_core
Rasa Core - Version: 0.12.2

pip show rasa_nlu
0.13.8

pip show tensorflow
Version: 1.10.0

Known Error
rasa_core.exceptions.UnsupportedDialogueModelError: The model version is to old to be loaded by this Rasa Core instance. Either retrain the model, or run withan older version. Model version: 0.11.3 Instance version: 0.12.2 Minimal compatible version: 0.12.0

pip install -U rasa_core==0.11.11


## Process to Run this

Step-1 Train Rasa NLU (Intent, Entity)
```
python -m rasa_nlu.train -c nlu_config.yml --data nlu.md -o models --fixed_model_name nlu --project current --verbose
```

Step-2 Generate Dialogs using Rasa Core (Flow)
```
python -m rasa_core.train -d domain.yml -s stories.md -o models/dialogue
```

Step-3 Run this Rasa Core Server
```
python -m rasa_core.run -d models/dialogue -u models/current/nlu
```

Step-4 Start Bot and start chatting
```
python bot.py
```
