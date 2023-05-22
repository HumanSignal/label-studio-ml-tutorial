# label-studio-ml-tutorial
Label Studio Machine Learning Tutorial

## Setting up the environment

```
python3 -m venv .venv
```

## Generating pre-labeled data

```
cd sentiment_analysis
python3 generate_predictions.py \
  ../IMDB_train_labeled_100.csv \
  ../IMDB_predictions_100.json
cd ..
```

## Launching the ML backend

```
# generate the backend template
label-studio-ml init \
  mlbackend \
  --script sentiment_analysis/sentiment_api.py

# copy required files to the template directory
cp sentiment_analysis/sentiment_cnn.py mlbackend/.
mkdir mlbackend/data
cp sentiment_analysis/data/* mlbackend/data/.

cd mlbackend

# launch the ml backend
label-studio-ml start .
```
