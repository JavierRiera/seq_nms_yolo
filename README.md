This project combines **YOLOv2**([reference](https://arxiv.org/abs/1506.02640)) and **seq-nms**([reference](https://arxiv.org/abs/1602.08465)) to realise **real time video detection**.

## Steps
0. This code works for a conda enviroment using python 2.7. to create a conda enviroment with the needed packages installed open the terminal and use the next instructions:

          conda create --name yolo_seqnms_env python=2.7
          
activate the enviroment:

          source activate
          conda activate yolo_seqnms_env

install the following packages:

          cv2:                conda install -c conda-forge opencv
          matplotlib:         conda install matplotlib
          Pillow:             conda install Pillow
          scipy:              conda install -c conda-forge scipy
          tensorflow:         conda install tensorflow
          object_detection:   conda install -c conda-forge tf_object_detection
          
          

1. clone the github repository in the directory you want executing the following instruction from terminal in the desired folder:

          git clone https://github.com/JavierRiera/seq_nms_yolo.git
          
          
2. go to the root directory (/seq_nms_yolo) and `make` the project;

3. Download `yolo.weights` and `tiny-yolo.weights` by running `wget https://pjreddie.com/media/files/yolo.weights` and  `wget https://pjreddie.com/media/files/yolov2-tiny-voc.weights`

4. Copy a video file to the video folder, for example, `input.mp4`;

5. In the video folder, run `python video2img.py -i input.mp4` and then `python get_pkllist.py`;

6. Return to root folder and change line 37 in yolo_detection.py to 


          lib = CDLL("xx/libdarknet.so", RTLD_GLOBAL) 
          
          
   where xx is the root folder rute of the proyect
   
7.  Run `python yolo_seqnms.py` to generate output images in `video/output`;

8. If you want to reconstruct a video from these output images, you can go to the video folder and run `python img2video.py -i output`

And you will see detection results in `video/output`

## Reference
This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).
