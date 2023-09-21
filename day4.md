

1단계 아나콘다 설치

wget https://repo.anaconda.com/archive/Anaconda3-2023.07-2-Linux-x86_64.sh

or

wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh

chmod 777 Anaconda3-2023.07-2-Linux-x86_64.sh
or
bash Anaconda3-2023.07-2-Linux-x86_64.sh

conda update pip
or 
conda install conda=23.7.4

conda env list

conda create py27 python=2.7
conda activate py27
pip install dronekit
pip install dronekit-sitl


참조1    https://jongsky.tistory.com/21

참조2  https://snowdeer.github.io/python/2018/01/01/make-env-of-anaconda/



http://www.lxshaw.com/tech/linux/2021/04/20/%E5%9C%A8ubuntu20-04%E4%B8%8B%E5%AE%89%E8%A3%85ardupilot/
