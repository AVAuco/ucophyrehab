# UCO Physical Rehabilitation dataset
The proposed dataset, coined “UCO Physical Rehabilitation”, has been recorded from June to July 2022. A total of 27 subjects (7 females and 20 males), in a range of age from 23 to 60 years, were recorded indoors in a controlled environment.
Subjects were instructed to perform four exercises for the lower-body and four exercises for the upper-body in both sides (left and right), obtaining a total of 16 different activities (see Figure 1). Each activity consists of four repetitions of the same exercise at a low speed to simulate a recent surgery or injury. These exercises are summarized in Table 1, classified by position, lower or upper body and side or orientation of the subject.
Hence, the dataset contains the following cases:
- Exercises 01 and 05 - Starting in a seated position, raise the leg as high as possible.
- Exercises 02 and 06 - In the same position as above, raise the leg as high as possible with the support of the other leg for raising and lowering.
- Exercises 03 and 07 - Lying flat on the treatment couch, raise the leg straight up as high as possible.
- Exercises 04 and 08 - In the same position as above, bend the knee with your heel on the treatment couch as much as possible.
- Exercises 09 and 13 - Seated in a chair, raise both arms straight as high as possible.
- Exercises 10 and 14 - Standing in front of the cameras, open and close both arms straight with a light weight.
- Exercises 11 and 15 - Standing in the same place as above, with elbows close to the body, stretch the rubber band with shoulder rotation.
- Exercises 12 and 16 - Standing in front of the treatment couch, with the other hand resting on the treatment couch, perform a pendulum shoulder rotation.

Overall, 2160 video sequences, with an average duration of 30.4 seconds (about 1.6M frames in total), were recorded with 5 RGB camera of 1280×720 pixel resolution. Each camera has recorded a different point of view of the scene.
The cameras were placed in 3 different angles and 3 different heights. The Figure 2 shows the camera set up. Cameras 0, 1 and 2 have the same horizontal angle with respect to the scene, but each one is placed at a different height. Camera 0 is situated 15 cm above the ground and camera 1 at 180 cm. The rest of the cameras were placed 100 cm above the ground.
At the same time, the scene was recorded with an IR motion capture system (OptiTrack) with 6 cameras placed in an elevated position, as we can see in the Figure 2. Subjects were fitted with infrared sensors on the shoulder, elbow and wrist for upper body exercises and on the hip, knee and ankle for the lower body exercises. These IR sensors provide the 3D ground-truth points for each record on the dataset. Subsequently, we obtain the 2D ground-truth points from these 3D ground-truth points by
projection.

## Dataset structure
The raw data and video sequences are stored in the `data`folder. This folder contains the following subfolders and files:
```
.
+-- dataset_2d.json
+-- dataset_3d.json
+-- data
|   +-- 0
|	|	+-- 01
|	|	|	+-- cam0.avi
|	|	|	+-- cam0_p2d.txt
|	|	|	+-- cam1.avi
|	|	|	+-- cam1_p2d.txt
|	|	|	+-- cam2.avi
|	|	|	+-- cam2_p2d.txt
|	|	|	+-- cam3.avi
|	|	|	+-- cam3_p2d.txt
|	|	|	+-- cam4.avi
|	|	|	+-- cam4_p2d.txt
|	|	|	+-- p3d.txt
|	|	+-- 02
|	|	+-- ...
|	|	+-- 16
|   +-- 1
|	+-- ...
|   +-- 27
```

### dataset_2d.json

### dataset_3d.json
