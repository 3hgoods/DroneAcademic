


day1.md

git clone --recurse-submodules https://github.com/ArduPilot/ardupilot.git

bash ./ardupilot/Tools/environment_install/install-prereqs-ubuntu.sh -y

*버전이 안맞는 에러후 아래 실행하고 다시 들어가니 되었다. 
. ~/.profile

cd $ARDUPILOT_HOME # the top-level of an ArduPilot repository
$ ./waf list_boards | grep 'fmuv3'

./waf configure --board fmuv3
./waf copter --upload

$ ./waf list | grep 'examples'

cd $ARDUPILOT_HOME # the top-level of an ArduPilot repository
./waf configure --board sitl
./waf build --target examples/RCProtocolDecoder


cd $ARDUPILOT_HOME # the top-level of an ArduPilot repository
./waf list | grep 'examples'

./waf configure --board=Pixhawk1
./waf build --target examples/INS_generic --upload



$ cd ardupilot/
~/ardupilot$ ./waf list_boards




$ cd ardupilot/

$ ./waf configure --board fmuv3
:~/ardupilot$ 

//아두콥터를 컴파일함 
./waf copter
