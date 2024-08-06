---
layout: page
title: Future Video Frame Prediction
description: using an image segmentation and a diffusion model
img: assets/img/dl.jpeg
importance: 4
category: work
---

[[Project Paper]]({{ '/assets/pdf/DLPaper.pdf' | relative_url }})
[[Project Presentation Slides]]({{ '/assets/pdf/DLPresentation.pdf' | relative_url }})
[[Code]](https://github.com/Spielerr/Paradigm-Future-Video-Frame-Prediction)  

### Abstract
Video frame prediction is one of the challenging task in machine learning. Predicting high quality images is still an evolving area in the field of generative artificial intelligence. The task for this report was to predict the 22nd frame given only the first 11 frames of a video consisting on multiple small objects of different shapes. In this work, for video future frame prediction we used a framework called Masked Conditional Video Diffusion (MCVD) which uses a probabilistic conditional score-based denoising diffusion model, conditioned on past 12 frames in a sliding window manner. For the image semantic segmentation, we used U-Net architecture that consists of series of down and up convolutions.

### Methodology
In our project, we aimed to tackle the challenge of video frame prediction and subsequent segmentation. This involved two main components: generating future frames from existing video sequences, and performing image segmentation on those frames. 

#### Future Frame Generation using MCVD 
The first part of our methodology utilizes the Masked Conditional Video Diffusion (MCVD) model. MCVDisapowerful tool for video synthesis tasks, which includes the capability to predict future video frames. It works by learning a distribution of video data and then generating frames that are likely to succeed the given sequence. This is particularly useful in scenarios where understanding future states of a dynamic scene is crucial. The MCVD model uses a probabilistic approach, conditioning on past and/or future frames, to ensure that the generated frames are not only plausible but also coherent with the video context. 

#### Segmentation using U-Net 
After generating the future frames, the next step involves segmenting these frames to identify and classify different objects and regions within them. For this task, we employed the UNet model, a type of convolutional neural network that is highly effective for image segmentation tasks. UNet is designed to work well with fewer training images and to produce precise segmentations. It operates by using a contracting path to capture context and a symmetric expanding path that enables precise localization. This architecture is particularly adept at dealing with the nuances in the spatial hierarchy of images, which makes it ideal for segmenting the complex scenes depicted in the synthetically generated video frames. The integration of these models showcases a significant stride in video processing technology, offering both enhanced predictive capabilities and detailed analytical insights into the generated video content.

### Results

#### Segmentation Model Performance
Our UNet segmentation model demonstrated exemplary performance on the validation set, achieving an accuracy of over 96%. This high level of accuracy underscores the model’s ability to effectively delineate and classify various objects within the video frames, which is crucial for detailed scene understanding in numerous practical applications.

#### Future Frame Prediction
We evaluated the performance of our Masked Conditional Video Diffusion (MCVD) model in predicting future frames under different sampling scenarios: 
*  With 100 DDPM samplings, the model achieved a Jaccard index score of approximately 0.12. This score reflects the initial capability of our model to approximate the future state of the video scenes, albeit with a broad margin for improvement.
* Increasing the sampling to 500 improved the Jaccard index score to around 0.20, indicating enhanced prediction accuracy with more extensive sampling. This result suggests that higher sampling rates may be beneficial for capturing more nuanced details in video frame prediction. 
* A reduced model size, using approximately two-thirds of the original model capacity, resulted in a Jaccard score of about 0.06. This significant drop highlights the importance of model complexity in capturing the dynamics of video scenes effectively. 
* Our final approach with 1000 samplings achieved the best results with a Jaccard score of 0.36 on the validation dataset.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ffp1.png" title="example image" class="img-fluid rounded z-depth-1" style="width: 50%; height: auto;"%}
    </div>
</div>
<div class="caption">
    From left to right: Predicted frame, ground truth, Segmentation Mask of the 22nd Frame (Video 1)
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ffp2.png" title="example image" class="img-fluid rounded z-depth-1" style="width: 50%; height: auto;"%}
    </div>
</div>
<div class="caption">
    From left to right: Predicted frame, ground truth, Segmentation Mask of the 22nd Frame (Video 2)
</div>
