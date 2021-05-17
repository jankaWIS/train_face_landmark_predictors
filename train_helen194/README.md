# Prepare xml for dlib on HELEN dataset

Possible alternative is to use [imlab](https://github.com/davisking/dlib/tree/master/tools/imglab) to do the same job and create xml.

## The landmarks look like this
![test-git](https://user-images.githubusercontent.com/54404810/118451909-62c5a300-b6fe-11eb-9ad1-9db3bf614a27.png)


## Source files
* [dlib datasets](http://dlib.net/files/data/)
* [dlib code for training a shape predictor](http://dlib.net/train_shape_predictor.py.html)
* [HELEN dataset](http://www.ifp.illinois.edu/~vuongle2/helen/)
* [iBUG dataset](https://ibug.doc.ic.ac.uk/resources/facial-point-annotations/)

## What to find here
There is a Jupyter ntb which is creating xml file which can then be used to train a shape/landmark predictor using `dlib`. The source for the landmarks is the HELEN dataset with 194 facial landmarks. The idea is to get the face boxes from the 68 model and then add the coordinates of the 194 points. The folder contains besides the images, landmark coordinates and the ntb the following xml files:

* helen.xml -- extracted only HELEN image coordinates from the 68 point dataset labels_ibug_300W_test.xml
* helen_no_mirror_full.xml -- full HELEN dataset with 194 landmarks, contains no mirror images and in total 2330 items
* helen_no_mirror_path.xml -- the same as helen_no_mirror_full.xml just the path to the training and testing images is replaced to be just `images`
* helen_no_mirror_test.xml -- testing set (330 items) for the helen_no_mirror_path.xml
* helen_no_mirror_train.xml -- training set (2000 items) for the helen_no_mirror_path.xml
* labels_ibug_300W_test.xml -- the 68 point xml dataset used for training of the default `dlib` classifier
* training_set.csv and training_set.xlsx -- list of names used for training, see [HELEN training set](http://www.ifp.illinois.edu/~vuongle2/helen/data/trainnames.txt)
* annotations -- txt files with landmarks, contains label folder where the annotations are named as the image they represent
* images -- all images from the HELEN dataset


## What not to find here
The trained classifier. The size of it is too large to be shared but you can run it yourself on your machine.

## More resources

* [Train a classifier using the 68 model on a subset of the 68 marks](https://www.pyimagesearch.com/2019/12/16/training-a-custom-dlib-shape-predictor/)

* [dlib shape predictor docs](http://dlib.net/train_shape_predictor.py.html)

* [Training face landmark detector using OpenCV](https://docs.opencv.org/master/d6/d49/md__build_master-contrib_docs-lin64_opencv_contrib_modules_face_tutorials_face_landmark_face_landmark_trainer.html) -- only in c++

* [Improve accuracy -- stack post](https://stackoverflow.com/questions/36908402/dlib-training-shape-predictor-for-194-landmarks-helen-dataset)

