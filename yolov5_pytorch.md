

Install env and follow it

1단계 아나콘다 설치

wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
bash Anaconda3-2023.09-0-Linux-x86_64.sh
source .bashrc
conda env list

conda create -n yolov5_1 python=3.8
conda activate yolov5_1


#conda update pip
#or 
#conda install conda=23.7.4

2단계 PyTorch labelImg 설치

nvcc --version
#10.1

# https://pytorch.org/  check cuda

sudo apt-get install cuda-11-7

nvcc --version
#10.1

nvidia-smi
#CUDA Version: 12.2

# Install PyTorch
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia

# Install labelimg (git clone labelimg)
git clone https://github.com/tzutalin/labelImg

# Install deps.  for Ubuntu Linux
sudo apt-get install pyqt5-dev-tools
cd labelImg/
pip install -r requirements/requirements-linux-python3.txt
make qt5py3

#python3 labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]


3단계 yolo v5설치
git clone https://github.com/ultralytics/yolov5
cd yolov5
( run it first conda update pip )
pip install -r requirements.txt  

ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
geocoder 1.38.1 requires click, which is not installed.

conda update pip
pip install -r requirements.txt 

#not show error mes. but i dought

wget https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5x.pt

wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7-e6e.pt

wget https://6.soompi.io/wp-content/uploads/image/c97b47aabe284ae1918acae0184c63c4/dummy.jpeg?s=900x600&e=t
mv dummy.jpeg?s=900x600&e=t dummy.jpeg
python detect.py --weights yolov5x.pt --source ./dummy.jpeg



(yolov5_1) h1@h1:~/yolov5$ ls
benchmarks.py  CONTRIBUTING.md  hubconf.py  README.zh-CN.md   train.py        wget-log
bts.jpeg       data             LICENSE     requirements.txt  tutorial.ipynb  yolov5x.pt
CITATION.cff   detect.py        models      segment           utils
classify       export.py        README.md   setup.cfg         val.py
(yolov5_1) h1@h1:~/yolov5$ python detect.py --weights yolov5x.pt --source ./bts.jpeg
detect: weights=['yolov5x.pt'], source=./bts.jpeg, data=data/coco128.yaml, imgsz=[640, 640], conf_thres=0.25, iou_thres=0.45, max_det=1000, device=, view_img=False, save_txt=False, save_csv=False, save_conf=False, save_crop=False, nosave=False, classes=None, agnostic_nms=False, augment=False, visualize=False, update=False, project=runs/detect, name=exp, exist_ok=False, line_thickness=3, hide_labels=False, hide_conf=False, half=False, dnn=False, vid_stride=1
YOLOv5 🚀 v7.0-225-gbb9706e Python-3.8.18 torch-2.0.1 CUDA:0 (NVIDIA GeForce RTX 3050 Laptop GPU, 3902MiB)

Fusing layers... 
YOLOv5x summary: 444 layers, 86705005 parameters, 0 gradients
image 1/1 /home/h1/yolov5/bts.jpeg: 448x640 7 persons, 1 tie, 57.9ms
Speed: 0.7ms pre-process, 57.9ms inference, 83.3ms NMS per image at shape (1, 3, 640, 640)
Results saved to runs/detect/exp



training data download

https://universe.roboflow.com/university-bswxt/crack-bphdr


link have a some error, so i used the download *.zip as yolov5 for pytorch


further study

https://universe.roboflow.com/search?q=like:university-bswxt%2Fcrack-bphdr


# YOLOv5 Train
python train.py --data ./crack/data.yaml --cfg ./models/yolov5x.yaml --weights yolov5x.pt --batch 8 --worker 4 --epochs 200 --name crackv5

# YOLOv5 Detection Test
python detect.py --source ../DC_Combo/video/ --weights ./runs/train/DC_Combo200/weights/best.pt



경로 이슈


(yolov5_1) h1@h1:~/yolov5$ (yolov5_1) h1@h1:~/yolov5$ python train.py --data ./crack/data.yaml

Dataset not found ⚠️, missing paths ['/home/h1/yolov5/valid/images']


==>
data.yaml
train: /home/h1/yolov5/crack/train/images
val: /home/h1/yolov5/crack/valid/images

# full 경로를 적어주는게 가장 안전함.
실행경로
~/yolov5

새 명령
python train.py --data ./crack/data.yaml --cfg ./models/yolov5x.yaml --weights yolov5x.pt --batch 8 --worker 4 --epochs 200 --name crackv5


메모리 이슈


torch.cuda.OutOfMemoryError: CUDA out of memory. Tried to allocate 20.00 MiB (GPU 0; 3.81 GiB total capacity; 3.51 GiB already allocated; 17.44 MiB free; 3.59 GiB reserved in total by PyTorch) If reserved memory is >> allocated memory try setting max_split_size_mb to avoid fragmentation.  See documentation for Memory Management and PYTORCH_CUDA_ALLOC_CONF

(NVIDIA GeForce RTX 3050 Laptop GPU, 3902MiB)

==>
python train.py --data ./crack/data.yaml --cfg ./models/yolov5x.yaml --weights yolov5x.pt --batch 2 --worker 2 --epochs 200 --name crackv5e200


사용1

python detect.py --weights yolov5x.pt --source ./bts.jpeg

python detect.py --source ../DC_Combo/video/ --weights ./runs/train/DC_Combo200/weights/best.pt



yolo v7설치

conda create -n yolov7_1 python=3.8
conda activate yolov5_1


# clone YOLOv7 repository
cd {HOME}
git clone https://github.com/WongKinYiu/yolov7

# navigate to yolov7 directory and checkout u7 branch
cd {HOME}/yolov7
git checkout 44f30af0daccb1a3baecc5d80eae22948516c579

# navigate to seg directory and install python dependencies
cd {HOME}/yolov7/seg
pip install --upgrade pip
pip install -r requirements.txt

