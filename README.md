# Landcover segmentation with Segment Anything distilled to Linknet

One of significant issues with Segment Anything is its weight and inference time. To predict one frame you need 75 sec on Intel i5 CPU or 6 sec on Nvidia P100 GPU.

In this experiment I trained Linknet to act like SAM and got 0.25 sec/frame on 768x768 image instead 75 sec/frame with original SAM model on Intel i5 CPU. It means about 300 times speedup.

### But there are a lot of constraints:
- it works only for a particular terrotory
- it works only with particular zoom level
- it still not so accurate

![Automatic segmentation example](pic1.jpg?raw=true "Automatic segmentation example")

### Experiment pipeline
1. Grab imagery *1_get_data.ipynb*
   - download region from https://download.geofabrik.de
   - filter landcover classes you need
   - download imagery
2. Make prediction with SAM and store results *2_predict_data_with_sam.ipynb*
3. Train Linknet model *2_predict_data_with_sam.ipynb*
4. Make a new data sample with active learning approach
5. 
