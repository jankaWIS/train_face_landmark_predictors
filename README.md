# Train face landmark predictors
Summarises several methods of obtaining face landmarks.

## Motivation

### Too many sources
I have been for a long time looking for a good face landmark predictor. Good in a sence of being precise on still images. I have gone through many posts and methods and I would like to summarise here my findings. This field seems to be developing fast, although most of the applications are adapted for fast face and landmark detection. There are many papers and there are impossibly many sources (eg. check out this page [papers with code](https://paperswithcode.com/task/facial-landmark-detection), or this [kaggle](https://www.kaggle.com/c/facial-keypoints-detection/code)) but I have figured out that many are not working well or are not optimal. I will try to mention some and it's very likely that I have missed many, appologies in advance.

### Not that simple customisation
Another problem I was having was just slightly tweaking what already exist. For example, there is the [`dlib`](http://dlib.net/) library which is using the 68-point landmark predictor which is great. If one needs to change it a bit and for example remove some points, the way is described in [this post](https://www.pyimagesearch.com/2019/12/16/training-a-custom-dlib-shape-predictor/). But what if we want to train it on the HELEN dataset? Or add points? I have found this [github repo of codeniko](https://github.com/codeniko/shape_predictor_81_face_landmarks) who adds more points to the 68 mask but I really struggled adjusting or following his code and repo. For the first problem, using the [Helen dataset](http://www.ifp.illinois.edu/~vuongle2/helen/) (or any other from the iBUG page), there were just no tutorials or code showing how to do that. The best I found was a question on Stack [How to improve accuracy](https://stackoverflow.com/questions/36908402/dlib-training-shape-predictor-for-194-landmarks-helen-dataset) but again assuming that one has the xml file and somehow then tweaks the training. Specifically for that, I put here a Jupyter ntb with a training manual. Then I am also showing the OpenCV [Face Detection using Haar Cascades](https://docs.opencv.org/3.4/d2/d99/tutorial_js_face_detection.html) (another [example](https://learning.oreilly.com/library/view/hands-on-image-processing/9781789343731/c523fa59-36d1-4be0-bdef-84e22d045b58.xhtml)).

## Sources which I am not discussing (no specific order)
* [3DDFA](https://github.com/cleardusk/3DDFA) or more specifically [SAN](https://github.com/D-X-Y/landmark-detection/tree/master/SAN) is what I would need but fails on eyes in my case (actually, everything does). The relevant data folder is on [Google disc](https://drive.google.com/drive/folders/14f2lcJVF6E4kIICd8icUs8UuF3J0Mutd) and it has [Colab implementation](https://colab.research.google.com/drive/1OKciI0ETCpWdRjP-VOGpBulDJojYfgWv).

* [Face Landmarks Detection With PyTorch](https://towardsdatascience.com/face-landmarks-detection-with-pytorch-4b4852f5e9c4) -- good source with code and a link to [Colab ntb](https://colab.research.google.com/drive/1-28T5nIAevrDo6MwN0Qi_Cgdy9TEiSP_?usp=sharing).

* [Supervision-by-Registration: An Unsupervised Approach to Improve the Precision of Facial Landmark Detectors](https://github.com/facebookresearch/supervision-by-registration)

* 

### Problems - todo
Haar Cascades [fails on eyes](https://stackoverflow.com/questions/58780684/opencv-not-detecting-eyes-correctly) and is missing [nose and eyebrow features](https://stackoverflow.com/questions/9015498/need-haar-casscades-for-nose-eyes-lipsmouth). Many of the posts point to `dlib`, I have tried the 68 point face landmark detection as well but it also was not precise enough (again, many places do that, eg [dlib-github](https://github.com/davisking/dlib/blob/master/python_examples/face_landmark_detection.py),[dlib](http://dlib.net/face_landmark_detection.py.html), [training a custom predictor](https://www.pyimagesearch.com/2019/12/16/training-a-custom-dlib-shape-predictor/)).
