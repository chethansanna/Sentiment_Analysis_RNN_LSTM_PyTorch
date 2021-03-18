# Sentiment Analysis with Long Short-Term Memory (LSTM)

The Sentiment Analysis model is implement using a recurrent neural network specifically LSTM (Long Short-Term Memory). This model predicts if the movie review represents a 'positive' or a 'negative' sentiment. Using an RNN here, rather than a strictly feedforward network is more accurate since we can include information about the sequence of words.

## Data

The dataset has 25000 movie reviews along with its associated labels as either 'positive' or 'negative'.

---
## Network Architecture
The architecture for this network is shown below:

![network_diagram](https://user-images.githubusercontent.com/47500198/111670187-da1ea980-8817-11eb-9893-cdead009212a.png)

First, the words are passed to an embedding layer. An embedding layer is needed because there are tens of thousands of words, so a more efficient representation for the input data is necessary than one-hot encoded vectors. Instead of using a pre-trained Word2Vec model, it is good enough to just have an embedding layer and let the network learn a different embedding table on its own. In this case, the embedding layer is for dimensionality reduction, rather than for learning semantic representations.

After input words are passed to an embedding layer, the new embeddings will be passed to LSTM cells. The LSTM cells will add recurrent connections to the network and gives the ability to include information about the sequence of words in the movie review data.

Finally, the LSTM outputs will be fed to a sigmoid output layer. Here a sigmoid function is used because positive and negative = 1 and 0, respectively, and a sigmoid will output predicted, sentiment values between 0-1.

---

## Results

#### Training and validation data:

Epoch: 1/5... Step: 200... Loss: 0.547504... Val Loss: 0.586342 <br>
Epoch: 1/5... Step: 400... Loss: 0.599924... Val Loss: 0.527879 <br>
Epoch: 2/5... Step: 600... Loss: 0.613822... Val Loss: 0.558392 <br>
Epoch: 2/5... Step: 800... Loss: 0.374181... Val Loss: 0.452838 <br>
Epoch: 3/5... Step: 1000... Loss: 0.337049... Val Loss: 0.486345 <br>
Epoch: 3/5... Step: 1200... Loss: 0.304758... Val Loss: 0.439330 <br>
Epoch: 4/5... Step: 1400... Loss: 0.206904... Val Loss: 0.471228 <br>
Epoch: 4/5... Step: 1600... Loss: 0.387008... Val Loss: 0.439708 <br>
Epoch: 5/5... Step: 1800... Loss: 0.230577... Val Loss: 0.464881 <br>
Epoch: 5/5... Step: 2000... Loss: 0.336348... Val Loss: 0.456677 <br>


#### Testing data: 

Test loss: 0.472 <br>
Test accuracy: 0.815

#### Inference:

The following reviews were used for inference of the model:

**Review 1:** 'This movie had the best acting and the dialogue was so good. I loved it.' <br>
**Review 2:** 'The worst movie I have seen; acting was terrible and I want my money back.' <br>
**Review 3:** 'a big, brashly beautiful, grandiosely enjoyable one.' <br>
**Review 4:** 'the story isn’t very interesting or original , the plot is formulaic, the characters are boring and stereotypical.' <br>
**Review 5:** 'a great movie,  appealing to audience of every age.' <br>

Results of the above reviews:

**Ground truth:** Positive review **Prediction:**  Positive review 	 **Prediction value, pre-rounding:** 0.520384 <br>

**Ground truth:** Negative review **Prediction:**  Negative review 	 **Prediction value, pre-rounding:** 0.475639 <br>

**Ground truth:** Positive review **Prediction:**  Positive review 	 **Prediction value, pre-rounding:** 0.710473 <br>

**Ground truth:** Negative review **Prediction:**  Negative review 	 **Prediction value, pre-rounding:** 0.498521 <br>

**Ground truth:** Positive review **Prediction:**  Positive review 	 **Prediction value, pre-rounding:** 0.724536 <br>
