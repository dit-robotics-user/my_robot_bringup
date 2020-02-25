# 在開機時自動roslaunch的方法

* 請勿直接clone下來，這樣不會work

1. 安裝robot_upstart

    - 輸入指令：`sudo apt-get install ros-melodic-robot-upstart`

2. 創一個package(ex: my_robot_bringup)，並且在裡面建立launch資料夾

    - 在launch file裡面連接你想要的package

3. 將robot_upstart連接至你的launch file

    - 這一步執行完後會產生對應的.service檔案

    - 輸入指令：`rosrun robot_upstart install my_robot_bringup/launch/my_robot.launch --job my_robot_ros --symlink`

4. 開啟服務

    - 輸入指令：`sudo systemctl start my_robot_ros.service`

    - 這樣以後開機就會自動執行launch file了

5. 測試

    - 輸入指令：`rosnode list`

    - 基本上只要不是看到error就是設定成功了

6. 停止core

    - 輸入指令：`sudo systemctl start my_robot_ros.service`

    - 這樣roscore就會停下來了

7. 移除service

    - 輸入指令：`sudo systemctl disable my_robot_ros.service`
    
    - 以後開機就不會自動roslaunch了

8. 資料來源：

    - https://roboticsbackend.com/make-ros-launch-start-on-boot-with-robot_upstart/
