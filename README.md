# Classification of IT support tickets using LSTM
Oct. 2019

- Jean-Marc Orliaguet, jmo@chalmers.se 
- Andreas Jonassson, andreas@chalmers.se 
- Mahsa Eshtehardi, mahsae@chalmers.se

IT-Office, Chalmers University of Technology


## Background

The IT-office at Chalmers receives about 30000 support tickets from students and employees each year that are manually sorted and placed into queues for  handling by different competence groups. Being able to automate the task of placing tickets into queues would save significant amounts of work. 

In our work we have trained a neural network using a data-set with about 150 000 entries using supervised learning. Input features where the title and body of a ticket. 

Target was queue where the ticket was solved.  We conclude that using LSTM neural network with a multilabel classification layer is enough to reach 87-88 % accuracy when sorting tickets into 40 classes. This is result is very promising and by working on data quality the result could be improved further.

## Installation

python3 is required

```
$ git clone https://github.com/Chalmers-IT/ticket-classification.git

$ cd ticket-classification
$ pip install -r requirements.txt

```

## Generate random sample data

Only for testing. The generated test data are random samples

```
$ python generate-sample-data.py
```

## Train the model
```
$ python run.py
 
```

## Viewing tensorboard logs:

```
$ tensorboard --logdir logs

```

Open your web browser at http://localhost:6006

## Finding most common words
Some of the most common words should be added to the list of excluded words (see COMMON_WORDS in constants.py)
```
$ python get-common-words.py
```


# Accuracy

Validation and test accuracy is 87-88%

![Accuracy](accuracy.png)

```
--- Starting trial: run-20191027-093156
{'emb_size': 200, 'batch_size': 128, 'lstm_size': 100, 'max_seq_len': 500, 'max_nb_words': 50000, 'epochs': 10}

...

Epoch 9/10
92263/92263 [==============================] - 610s 7ms/step - loss: 0.2833 - accuracy: 0.9188 - val_loss: 0.5100 - val_accuracy: 0.8716
Epoch 10/10
92263/92263 [==============================] - 608s 7ms/step - loss: 0.2569 - accuracy: 0.9263 - val_loss: 0.5171 - val_accuracy: 0.8738
10252/10252 [==============================] - 33s 3ms/step
Test set
  Loss: 0.517
  Accuracy: 0.874
```

# References

- J.Brownlee, How to Develop a Bidirectional LSTM For Sequence Classification in Python with Keras, June. 2017. https://machinelearningmastery.com/develop-bidirectional-lstm-sequence-classification-python-keras/
- J.Brownlee, How to Clean Text for Machine Learning with Python, Aug. 2019. https://machinelearningmastery.com/clean-text-machine-learning-python/
- H.Heidenreich, Text Classification in Keras A Simple Reuters News Classifier, Aug. 2018.  https://towardsdatascience.com/text-classification-in-keras-part-1-a-simple-reuters-news-classifier-9558d34d01d3

- SLi, Multi-Class Text Classification with LSTM, Apr. 2019.  https://towardsdatascience.com/multi-class-text-classification-with-lstm-1590bee1bd17 
- TensorBoard: TensorFlow's visualization toolkit  https://www.tensorflow.org/tensorboard
