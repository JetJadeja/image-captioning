# image-captioning

Image Captioning Neural Network notebook using Keras. This project aims to develop an image captioning model that can generate a descriptive caption for an input image. The model utilizes a combination of deep learning techniques within computer vision and natural language processing in order to do this. You can view the notebook for this project in `image-captioning.ipynb` and an overview of the architecture below.

## Dataset Installation Instructions

In order to install the data, you can use the `install.ipynb` notebook, which will install the datasets from Kaggle, un-zip them, and put them into the `data` directory.

## Architecture Overview

The architecture of the model consists of the following components:

1. **MobileNetV2 CNN**: We utilize a pre-trained CNN to extract relevant features from the input image, resulting in a flattened features array, which is then encoded.

2. **Caption Input and Sequence Encoding Layers**: The input caption is processed using an embedding layer to convert words into vectors. Rather than manually training this layer, we actually use the GloVe (Global Vectors for Word Representation) dataset developed by Stanford.

3. **LSTM Layers**: Next, we use both bidirectional and standard LSTM layers to capture the contextual info (and dependencies) among words within the caption. This allows the model to better the structure of the captions, resulting in far more coherent output sequences.

4. **Combining Image and Caption Inputs**: We then combine the output of the image feature encoders and the LSTM layers using an `Add` layer.

5. **Decoder Layers**: These encoded and processed information is then passed through a Dense layer with a `ReLu` activation function for further processing.

6. **Output Layer**: Finally, we use a dense layer with a softmax activation function to predict the next word in the caption.

Our model takes in two inputs: the image's features and the partial caption, generating a single output, which is the next word in the caption. By using the pre-trained MobileNet V2 CNN and LSTM layers, the model combines computer vision and nlp techniques to generate accurate captions for images.
