# Traffic Sign Detection

[//]: # (Image References)
[image1]: ./project_images/overview.jpg
[image2]: ./project_images/all.jpg
[image3]: ./project_images/training.jpg
[image4]: ./project_images/all_org.jpg
[image5]: ./project_images/threshold_all.jpg
[image6]: ./project_images/sliding_window.jpg
[image7]: ./project_images/threshold_img.jpg
[image8]: ./project_images/thresholded_windows.jpg

![alt text][image1] <br/>

See also: <https://github.com/jawilk/SDCND-P2-Traffic-Sign-Classifier>


## Final

## Training
For training the model a combination of own images and images from the german traffic sign dataset were used (see "Sources" below). The model was trained with 6 classes:
* 0 Background
* 1 50 km/h
* 2 Priority
* 3 Stop
* 4 Dangerous Curve Right
* 5 No Passing

Training took me around 1 1/2h on my local CPU. After 25 Epochs the model achieved:
* Train acc: 0.9734
* Train loss: 0.0881
* Validation acc: 0.9832
* Validation loss: 0.0756

![alt text][image2] ![alt text][image3]

## Extraction of region proposals

![alt text][image4] ![alt text][image5]

See also: <https://github.com/jawilk/SDCND-P5-Vehicle-Detection>

A sliding window approach was used to extract regions of interest.

![alt text][image6] ![alt text][image7] ![alt text][image8]

## Run
### Create training data
**new_data.py** contains code for creating a new pickle file of an image folder, the dict dumped to the file has the stucture:
> 'features': img_data, 'labels': labels

For instance, if you have a folder structure like this:


|-- images<br/>
---|-- 50_kmh<br/>
---|-- background<br/>
---|-- no_passing<br/>
---|-- priority<br/>
---|-- right_curve<br/>
---|-- stop<br/>
```python
python new_data.py 0 background
```
This will create "background.p" in the "images" dir, containing all images from the background folder with assigned label 0. Proceeding like this for the other folders/labels will yield 6 "folder_name.p" files.<br/>
To combine all into one single "traffic_sign_all.p" file which **train_model_traffic_sign.py** takes as input, type:
```python
python save_single_file.py traffic_sign_all
```
The final file I used can be found in **"data/"**.


## Sources
* German Traffic Sign Dataset:
 J. Stallkamp, M. Schlipsing, J. Salmen, and C. Igel. The German Traffic Sign Recognition Benchmark: A multi-class classification competition. In Proceedings of the IEEE International Joint Conference on Neural Networks, pages 1453–1460. 2011.
 <http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset>
 
* Radu Timofte, Karel Zimmermann, Luc Van Gool. Multi-view traffic sign detection, recognition, and 3D localisation. 
 <http://www.vision.ee.ethz.ch/~timofter/publications/Timofte-WACV-2009.pdf>
 
* Similar project using SVMs with HOG features:
 <https://github.com/AutoModelCar/AutoModelCarWiki/wiki/traffic-sign-detection> 
