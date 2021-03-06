# coffee_machine

Behavior tree implementation of making a coffee using the package  [BehaviorTree.CPP](https://github.com/BehaviorTree/BehaviorTree.CPP).

Actions and conditions of this behavior are used to see if the human is handling some object in the following way.

 1. First, it detects the human left ant right wrist using the package [openpose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) merged in ROS with the package [openpose_ros](https://github.com/firephinx/openpose_ros).
 2. Second, the neural network [darknet](https://github.com/pjreddie/darknet) has been trained in order to detect the following objects:
       - milk
       - coffee
       - coffee maker
       - cup
       - sugar
       - marro_tank
       - water_tank

    In order to use this pretrained model with ROS, the package [darknet_ros](https://github.com/leggedrobotics/darknet_ros) has been used.
 3. Once the human pose and object is detected, an algorithm has been developed in order to detect if the person is handling the object. 

 Bag files can be found in the three tests folder. It can be found in [rosbag_files](https://drive.google.com/drive/folders/15Y5ckfjOt-66Ck-eKTsaKYBuWFjE0j34?usp=sharing).



## To run the code

1. Launch in one terminal the following launch file:
    - *roslaunch coffee_machine coffee_machine.launch*
2.  Launch in other terminals the following launch file:
    - *roslaunch coffe_machine coffee_machine_darknet_openpose.launch*
3. In another terminal window, make a rosbag play of the test that you would like to test:
    - *rosbag play primera_prova.bag*
4. In another terminal window, make an echo of the topic *\coffee_machine\Feedback*. This will show the state of behaviour tree.
    - *rostopic echo /coffe_machine/Feedback*


An example can be found here:

![picture](test_1_IsWaterTankRemoved.png)