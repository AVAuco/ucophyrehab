# UCO Physical Rehabilitation dataset
<p><a href="https://www.mdpi.com/1424-8220/23/21/8862"><img src="https://img.shields.io/badge/READ-the_paper-blue"></a> &nbsp; <img src="https://img.shields.io/twitter/follow/ucoava">
</p>


The proposed dataset, coined “UCO Physical Rehabilitation”, has been recorded from June to July 2022. A total of 27 subjects (7 females and 20 males), in a range of age from 23 to 60 years, were recorded indoors in a controlled environment in the [AVA group](https://www.uco.es/investiga/grupos/ava/) at the University of Cordoba.

![Examples of some of the exercises included in the dataset: (a) Exercise 01, (b) Exercise 02, (c) Exercise 03, (d) Exercise 04, (e) Exercise 13, (f) Exercise 14, (g) Exercise 15, (h) Exercise 16. All views from the camera 2 viewpoint.](https://raw.githubusercontent.com/AVAuco/ucophyrehab/b956be91c52c689580fd245ccf56506b76d797b7/img/dataset_web_pixel.png)

> Figure 1 - Examples of some of the exercises included in the dataset: (a) Exercise 01, (b) Exercise 02, (c) Exercise 03, (d) Exercise 04, (e) Exercise 13, (f) Exercise 14, (g) Exercise 15, (h) Exercise 16. All views from the camera 2 viewpoint.

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

| ID | Exercise name | Position | Side | Upper / Lower body |
|--|--|--|--|--|
| 01 | Bending the knee without support while sitting | Seated | Left | Lower |
| 02 | Bending the knee with support while sitting | Seated | Left | Lower |
| 03 | Lift the extended leg | Supine | Left | Lower |
| 04 | Bending the knee with bed support | Supine | Left | Lower |
| 05 | Bending the knee without support while sitting | Seated | Right | Lower |
| 06 | Bending the knee with support while sitting | Seated | Right | Lower |
| 07 | Lift the extended leg | Supine | Right | Lower |
| 08 | Bending the knee with bed support | Supine | Right | Lower |
| 09 | Shoulder flexion | Seated | Left | Upper |
| 10 | Horizontal weighted openings | Standing | Left | Upper |
| 11 | External rotation of shoulders with elastic band | Standing | Left | Upper |
| 12 | Circular pendulum | Standing | Left | Upper |
| 13 | Shoulder flexion | Seated | Right | Upper |
| 14 | Horizontal weighted openings | Standing | Right | Upper |
| 15 | External rotation of shoulders with elastic band | Standing | Right | Upper |
| 16 | Circular pendulum | Standing | Right | Upper |

> Table 1 - List of exercises included in the UCO Physical Rehabilitation dataset. They are classified by
position, side and upper/lower body.

Overall, 2160 video sequences, with an average duration of 30.4 seconds (about 1.6M frames in total), were recorded with 5 RGB camera of 1280×720 pixel resolution. Each camera has recorded a different point of view of the scene.
The cameras were placed in 3 different angles and 3 different heights. The Figure 2 shows the camera set up. Cameras 0, 1 and 2 have the same horizontal angle with respect to the scene, but each one is placed at a different height. Camera 0 is situated 15 cm above the ground and camera 1 at 180 cm. The rest of the cameras were placed 100 cm above the ground.

![Plan of the cameras in the laboratory. The scheme shows both the location of the OptiTrack motion capture system (solid blue lines) and the RGB cameras (solid red lines).](https://raw.githubusercontent.com/AVAuco/ucophyrehab/main/img/plano_lab_v2_3d.png)

> Figure 2 - Plan of the cameras in the laboratory. The scheme shows both the location of the OptiTrack motion capture system (solid blue lines) and the RGB cameras (solid red lines).

At the same time, the scene was recorded with an IR motion capture system (OptiTrack) with 6 cameras placed in an elevated position, as we can see in the Figure 2. Subjects were fitted with infrared sensors on the shoulder, elbow and wrist for upper body exercises and on the hip, knee and ankle for the lower body exercises. These IR sensors provide the 3D ground-truth points for each record on the dataset. Subsequently, we obtain the 2D ground-truth points from these 3D ground-truth points by
projection.

## Dataset structure
The raw data and video sequences are stored in the `data` folder. This folder contains the following subfolders and files:
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
The first level of subfolders corresponds with all of the 27 individuals participants in the dataset. Each individual folder contains 16 subfolders, one for each exercise they performed. In each exercise folder, we can find a `camX.avi` and a `camX_p2d.txt` file for each camera and a `p3d.txt` file. The `camX_p2d.txt` contains the joints coordinates 
### dataset_2d.json
In Figure 3 you can see the structure of the dataset JSON for 2D. This is the first individual (folder), the first camera and the first frame of the record.
![Structure of the dataset JSON for 2D](https://raw.githubusercontent.com/AVAuco/ucophyrehab/main/img/ucophyrehab_2d.png)
> Figure 3 - Structure of the dataset JSON for 2D.


### dataset_3d.json
In Figure 4 you can see the structure of the dataset JSON for 3D. This is the first individual (folder) and the first frame of the record.
![Structure of the dataset JSON for 3D](https://raw.githubusercontent.com/AVAuco/ucophyrehab/main/img/ucophyrehab_3d.png)
> Figure 4 - Structure of the dataset JSON for 3D.

# Citation
```
@Article{aguilar_2023,
  AUTHOR = {Aguilar-Ortega, Rafael and Berral-Soler, Rafael and Jiménez-Velasco, Isabel and Romero-Ramírez, Francisco J. and García-Marín, Manuel and Zafra-Palma, Jorge and Muñoz-Salinas, Rafael and Medina-Carnicer, Rafael and Marín-Jiménez, Manuel J.},
  TITLE = {UCO Physical Rehabilitation: New Dataset and Study of Human Pose Estimation Methods on Physical Rehabilitation Exercises},
  JOURNAL = {Sensors},
  VOLUME = {23},
  YEAR = {2023},
  NUMBER = {21},
  ARTICLE-NUMBER = {8862},
  URL = {https://www.mdpi.com/1424-8220/23/21/8862},
  ISSN = {1424-8220},
  DOI = {10.3390/s23218862}
}
```

# Download
If you want to download this dataset, please write an email to the following address: [inforeha@uco.es](mailto:inforeha@uco.es) with your name, affiliation and research purposes.

Website: https://www.uco.es/investiga/grupos/ava/portfolio/ucophyrehab/

Paper: https://www.mdpi.com/2542956
