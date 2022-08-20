# Attention-Based Residual U-Net for Brain MRI Segmentation



Using a standard U-Net architecture with skip connections embedded in residual blocks and enriched with attention for creating a robust Deep Learning model for segmenting tumors in brain MRI scans.


## Sample Prediction Results on Unseen Data

![]('miscellaneous/Sample Prediction on Unseen Data.png')

## Dataset

The dataset used for this project is taken from Kaggle (<a href = "https://www.kaggle.com/datasets/mateuszbuda/lgg-mri-segmentation">dataset</a>).

The dataset consists of brain MR images together with manual FLAIR abnormality segmentation masks. The images were obtained from The Cancer Imaging Archive (TCIA).
They scans correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection. The dataset is contains nearly 6400 brain MRI Images.

## Network Architecture

* A series of convolutional layer – batch normalization layer - convolutional layer – batch normalization layer is considered as a conv_block. 
* A conv_block with skip connections is called a res_conv_block.
* A attention block is also used which basically takes 2 inputs: i) the gating signal which comes from a layer below the current layer in the decoder path and ii) the input from the skip connection path going from the encoder to the decoder(as in traditional U-Net framework). After a series of computation followed by concatenation of these inputs, the resultant output from an attention block is a set of pixel-level weights.
* A series of res_conv_block are used; each followed by maxpooling layers in the encoder path.
* The decoder path consists of a bunch of attention blocks, res_conv_blocks, upsampling and concatenation layers.
* BinaryFocalLoss is used as the loss function and Adam is used as the optimizer.


## Tech Stack

* Tensorflow
* Keras
* OpenCV
* Pillow 


## Feedback

If you have any feedbacks or queries, feel free to reach me out at: aaryan.nakhat@gmail.com

If you would like to connect/collobrate with me, do ping me up on Linkedln: <a href = "https://www.linkedin.com/in/aaryan-nak" target="_blank">Aaryan Nakhat</a>


