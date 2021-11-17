# Traffic-Signs-Recognition
When considering about autonomous vehicles it is very important to recognize traffic signs in real time. This project is for traffic sign recognition using deep learning for real time video feed.


> ***Trafic Sign Classes***

1. `Speed limit (20km/h)`
2. `Speed limit (30km/h)`
3. `Speed limit (50km/h)`
4. `Speed limit (60km/h)`
5. `Speed limit (70km/h)`
6. `Speed limit (80km/h)`
7. `End of speed limit (80km/h)`
8. `Speed limit (100km/h)`
9. `Speed limit (120km/h)`
10. `No passing`
11. `No passing veh over 3.5 tons`
12. `Right-of-way at intersection`
13. `Priority road`
14. `Yield`
15. `Stop`
16. `No vehicles`
17. `Veh > 3.5 tons prohibited`
18. `No entry`
19. `General caution`
20. `Dangerous curve left`
21. `Dangerous curve right`
22. `Double curve`
23. `Bumpy road`
24. `Slippery road`
25. `Road narrows on the right`
26. `Road work`
27. `Traffic signals`
28. `Pedestrians`
29. `Children crossing`
30. `Bicycles crossing`
31. `Beware of ice/snow`
32. `Wild animals crossing`
33. `End speed + passing limits`
34. `Turn right ahead`
35. `Turn left ahead`
36. `Ahead only`
37. `Go straight or right`
38. `Go straight or left`
39. `Keep right`
40. `Keep left`
41. `Roundabout mandatory`
42. `End of no passing`
43. `End no passing veh > 3.5 tons`


> ***Dataset - [kaggle](https://www.kaggle.com/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign)***

------------------------------------------

> ***Steps***

* Since data set has several sizes, it will be difficult when model training.
* Therefore as 1st step resize the whole dataset to `32 x 32 x 3`
* Then convert above created list into `numpy arrays` that helps to model to training
* After splitting the data set as training and testing check the shape of the data sets.
    * `train_x.shape (26270, 32, 32, 3)`
    * `validation_x.shape (12939, 32, 32, 3)`
    * `train_y.shape (26270,)`
    * `vallidation_y.shape (12939,)`

* Since we consider 43 classes and both train and validation y is 1D array, we have to reshape by using encoding
    * `train_y = tf.keras.utils.to_categorical(train_y, num_classes=num_classes)`
    * `val_y = tf.keras.utils.to_categorical(val_y, num_classes=num_classes)`
    *  *This function returns a matrix of binary values (either ‘1’ or ‘0’). It has number of rows equal to the length of the input vector and number of columns equal to the number of classes.*
    *  After that, the shapes are,
        * `train_y.shape (26270, 43)`
        * `val_y.shape (12939, 43)`

* Image data Augmentation is done.
* Build the model as follows,
    * Use `convolutional layers`, `Maxpooling`, `Dropout`, `Flatten`, `Dense`. You can refer [model training](https://github.com/AvishkaSandeepa/Traffic-Signs-Recognition/blob/master/main/codes/model-trainig.ipynb) python code for further details.
    * That model gives the very high accuracies and low losses
        * `training loss = 3.17%`
        * `Validation loss = 0.40%`
        * `training accuracy = 99.18%`
        * `training accuracy = 99.91`


-----------------------------------------------------

> ***Resultant Graphs***

* Graph of the training results,

<img src="https://github.com/AvishkaSandeepa/Traffic-Signs-Recognition/blob/master/main/codes/losses-accuracies.png" alt="Accuracies and Losses" style="width:1000px;"/>

