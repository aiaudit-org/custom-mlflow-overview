# Steps

## Make front end changes
1. Adjust App.css and App.js

## Build pip wheel
1. Fulfill reqs as described here https://github.com/mlflow/mlflow/blob/master/CONTRIBUTING.rst#common-prerequisites-and-dependencies
``
conda create --name mlflow-dev-env python=3.6
pip install -r dev-requirements.txt
pip install -r test-requirements.txt
pip install -e .[extras]  # installs mlflow from current checkout
pip install pytest
``
1. Also Javascript dependencies
``
cd mlflow/server/js
npm install
cd - # return to root repository directory
``
1. Build a dstributable artifcat https://github.com/mlflow/mlflow/blob/master/CONTRIBUTING.rst#building-a-distributable-artifact
   1. Generate JS files in mlflow/server/js/build
   ``
   cd mlflow/server/js
   npm run build
   ``
   1. Build a pip-installable wheel in dist/:
   ``
   cd -
   python setup.py bdist_wheel
   ``

## Install pip wheel (it is in /dist)
``
pip install file.whl
``

## Run mlflow as usual
``
mlflow server
``

## Troube shooting
1. Update pandas
``
pip install pandas -U
``
1. Cannot find module 'caniuse-lite/dist/unpacker/agents' when running create react app
``
npm i caniuse-lite
``

# Inside aws mlflow cloud formation
1. Adjust Dockerfile to wget and install custom wheel
2. Rest as normal


regular aws-mlflow: https://github.com/aws-samples/amazon-sagemaker-mlflow-fargate
project based mlflow example with wheel: https://github.com/aiaudit-org/mlflow-pm
itu aws-mlflow: https://github.com/aiaudit-org/amazon-sagemaker-mlflow-fargate
itu aws-mlflow w/ project based mflow wheel: https://github.com/aiaudit-org/mlflow-aws-pm
