# Image classifier using Tensorflow #
This is an image classifier I worked on using 'Tensorflow'.
Its used to classify images into 3 types.

## Prerequisites ##
* The files required for this are given in my google drive, the link is: https://drive.google.com/file/d/0B-Y8en_pSPeiZUc4LUJRdTdTVUk/view?usp=sharing

* You also need Tensorflow library, which can be instaled using:
    ``` 
    pip install tensorflow
    ```
* Also i worked on linux

## How to use it ##
* First extract the .zip file given in my google drive page
* Next open the terminal over there
* Now we're going to classify this image:
  ![Alt text](sample_images/big_boss.jpg?raw=true "Optional Title")
  
  As one of these 3 images:
  ![Alt text](sample_images/3_images.png?raw=true "Optional Title")
  
* To do that we use the command 
  ```
  python -m scripts.label_image \
    --graph=tf_files/retrained_graph.pb  \
    --image=tf_files/metalgear_snake/big_boss.jpg
  ```
  This is because the 'label_image.py' is the code used to classify the image,
  
  and 'tf_files/metalgear_snake/big_boss.jpg' is the location of the image we need to classify
* This gives the output as:

    ![Alt text](sample_images/final_output.jpeg?raw=true "Optional Title")
  
## How I trained the data ##

* I first opened the terminal in the folder which gets extracted from the zip
* To collect all the images i just downloaded the first 100 images from the google search using this chrome extension:https://chrome.google.com/webstore/detail/fatkun-batch-download-ima/nnjjahlikiabnchcpehcpkdeckfgnohf?hl=en
* Then typed the following commands to train the data:
  ```
  IMAGE_SIZE=224
  ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"
  ```
  ```
  python -m scripts.retrain \
    --bottleneck_dir=tf_files/bottlenecks \
    --how_many_training_steps=500 \
    --model_dir=tf_files/models/ \
    --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}" \
    --output_graph=tf_files/retrained_graph.pb \
    --output_labels=tf_files/retrained_labels.txt \
    --architecture="${ARCHITECTURE}" \
    --image_dir=tf_files/metalgear_snake
  ```
* This took me about 10 minutes to train, then I used the above methods to classify the image

* I used this website as a base for my understanding of the code:https://goo.gl/QTwZ3v



