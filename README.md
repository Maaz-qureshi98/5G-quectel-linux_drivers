# Install drivers inside the Workstation used Linux OS (Ubuntu 22.04 LTS)
Step 0:
1. Update firmware
2. cd QFirehose_Linux_Android_V1.4.16/
3. sudo ./QFirehose -f ../firmware/update/firehose/

Step 1:
1. Compile and install kernel module
2. sudo modprobe qmi_wwan_q

Step 2: MAIN STEP
Start driver
cd quectel
sudo ./Quectel_QConnectManager_Linux_V1.6.5/quectel-CM -4 -6 -s ltemobile.apn
//
# Install Cutecom software on workstation to check the 5G devices logs 
Atache the usd cable of device to worstation, allow the usb pot permission from the terminal, follow the below steps:
1. ls /dev/ttyUSB*
for permission: 
Step 1
1. sudo usermod -aG dialout m23qures 
execute the below
1. sudo chmod a+rw /dev/ttyUSB0
2. sudo chmod a+rw /dev/ttyUSB1
3. sudo chmod a+rw /dev/ttyUSB2
4. sudo chmod a+rw /dev/ttyUSB3

Step 2:
Open cutcom software in the wortstation 
1. select the devices: /dev/ttyUSB3

AT Commands Type insde the cotecom prompt window
1. ATI
2. at+cfun=0																											
3. at+cfun=1																											
4. at+cereg?																											
5. at+cops?

Some common commands used: 
in seperate terminal 
m23qures@maaz-robotics:~$ ip addr show 
m23qures@maaz-robotics:~$ ping -I wwan0 8.8.8.8
m23qures@maaz-robotics:~$ ping -I wwan0 robohub.eng.uwaterloo.ca
m23qures@maaz-robotics:~$ ping -I wwan0 -4 robohub.eng.uwaterloo.ca
m23qures@maaz-robotics:~$ scp -r quectel/
m23qures@maaz-robotics:~$ scp -r quectel/qmi_wwan/robohub@labwork5:robohub/quectel/qmi_wwan_patched
m23qures@maaz-robotics:~$ scp -r quectel/qmi_wwan robohub@labwork5:robohub/quectel/qmi_wwan_patched

//
# Install drivers inside the Robot ROS2 based setup below
1. ssh ubuntu@192.168.186.3
2. password: 
3. lsusb -t
4. lsusb -t -v
5. sudo journalctl -f -k
6. ip addr show
7. sudo nmcli
once:
8. wget https://robohub.eng.uwaterloo.ca/share/qconnect.tar.bz2
9. tar -axf qconnect.tar.bz2 
10. cd Quectel_QConnectManager_Linux_V1.6.5
11. make clean
12. make
13. cd ..
always:
14. sudo ./Quectel_QConnectManager_Linux_V1.6.5/quectel-CM -4 -6
or 
15. ubuntu@uwbot-05:~/Quectel_QConnectManager_Linux_V1.6.5$ sudo ./quectel-CM -4 -6

sudo ./quectel-CM -4 -6
[05-07_20:33:37:352] QConnectManager_Linux_V1.6.5


