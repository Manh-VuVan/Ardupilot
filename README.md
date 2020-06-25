# Hướng dẫn mô phỏng SITL X-Plane
An Ardupilot control model for QuadPlane flight simulation with X-Plane

## Giới thiệu
  Đây là dự án mô phỏng hệ thống điều khiển tự động cho UAV QuadPlane mã nguồn mở Ardupilot sử dụng nền tảng mô phỏng X-Plane.
## Tiến hành
### 1. Chuẩn bị môi trường phát triển:
- **1.1 Cài đặt X-Plane theo hướng dẫn ở đây: https://www.evernote.com/shard/s659/sh/4bfff893-1356-9ed0-3da8-be3b00f1a5a9/f106fd834ee6499e70ace57bcb7f8911**
- **1.2 Cài đặt Visual Studio Code: https://code.visualstudio.com/docs/setup/windows**
- **1.3 Cài đặt Windows Subsystem for Linux với retro Ubuntu 18.04 hoặc 20.04: https://docs.microsoft.com/en-us/windows/wsl/install-win10**
      ![Ubuntu retro](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/ubuntu.png?raw=true)
- **1.4 Cài đặt Mission Planner: https://ardupilot.org/planner/docs/mission-planner-installation.html**     
---       
### 2. Kéo dự án về local bằng Visual Studio Code với đường dẫn: https://github.com/binhnt94/ardupilot
  ![Github](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/github(1).png?raw=true)
  ![Github](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/github(2).png?raw=true)
  ![Github](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/github(3).png?raw=true)
  ![Github](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/github(4).png?raw=true)      

### 3. Chạy dự án
- **3.1 Mở dự án bằng cách nhấn Open.**
  ![open](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/open.jpg?raw=true)      
- **3.2 Mở dự án trong Windows Subsystem for Linux (WSL).**
  ![open in WSL](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/open-in-WSL.jpg?raw=true)      
- **3.3 Chọn retro Ubuntu.**
  ![Re-open in WSL](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/re-open-in-WSL.jpg?raw=true)      
  ![Ubuntu 18.04](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/18-04.jpg?raw=true)      
  ![Kết quả](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/ket-qua.jpg?raw=true)      
- **3.4 Chạy script khởi tạo môi trường.**
  ```shell
    $ cd Tools/environment_install/
    $ ./install-prereqs-ubuntu.sh 
  ```
- **3.5 Thoát ra thư mục dự án và chạy script mô phỏng**
  ```shell
  $ cd ..
  $ cd ..
  $ source ~/.profile
  $ sim_vehicle.py -v ArduPlane -f xplane
  ```
  > ở đây -v là tham số vehicle, -f là tham số frame
  Nếu biên dịch không báo lỗi nghĩa là chạy thành công thì tắt đi bằng tổ hợp phím Ctrl+C.
  ---
### 4. Chạy X-Plane với mô hình QuadPlane và sân bay 916 Hoa Lac.
- **4.2 Tìm đến phần Settings**
  --> tab Data Output --> NETWORK CONFIGURATION,
  đánh dấu tích vào ô Send network data output. Đặt IP address: 127.0.0.1
  Port 49005
- **4.3 Vẫn ở tab Data Output**
  Cài đặt các tham số data rate như hình:      
  ![Data rate](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/data-output.png?raw=true)
- **4.4 Tích chọn 1 trường dữ liệu bất kỳ**
  ![Chọn trường dữ liệu](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/select.png?raw=true)
- **4.5 Chọn máy bay và sân bay như hình minh họa**    
  ![Chọn chuyến bay mới](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/new-flight.png?raw=true)
  ![Bắt đầu chuyến bay mới](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/start.png?raw=true)
---
### 5. Tùy chọn: vận hành bay bằng cmd mavproxy hoặc GCS Mission Planner hoặc QgroundControl
- **5.1 Chạy lệnh sau để chạy script mô phỏng**
  ```shell
    $ sim_vehicle.py -v ArduPlane -f xplane       
  ```
  > ở đây -v là tham số vehicle, -f là tham số frame
- **5.2 Kết nối Mission Planner qua UDP: Baudrate 115200**
    ![Kết nối Mission Planner qua UDP](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/MP-udp.png?raw=true)
    ![Kết nối Mission Planner qua UDP](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/connect-MP.png?raw=true)
    ![Kết nối Mission Planner qua UDP](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/ok.png?raw=true)
- **5.3 Nạp tham số cấu hình cho Autopilot**
    ![Nạp tham số cấu hình](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/config.png?raw=true)
    ![Nạp tham số cấu hình](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/load.png?raw=true)
    ![Nạp tham số cấu hình](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/write.png?raw=true)
    ![Nạp tham số cấu hình](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/ok.png?raw=true)
- **5.4 Nạp nhiệm vụ bay cho Autopilot**
    ![Nạp nhiệm vụ bay](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/plan.png?raw=true)
    ![Nạp nhiệm vụ bay](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/load-wp.png?raw=true)
    ![Nạp nhiệm vụ bay](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/write-wp.png?raw=true)
- **5.5 Vận hành bay tự động cơ bản**
  - Khi cửa sổ dòng lệnh của Visual Studio Code hiện ra dòng: 
  ```shell
  APM: EKF2 IMU0 is using GPS
  APM: EKF2 IMU1 is using GPS
  APM: EKF3 IMU1 is using GPS
  APM: EKF3 IMU0 is using GPS
  ```
  nghĩa là Autopilot đã khởi động xong.
  - Ta tiến hành đặt WP khởi đầu và mode bay cho máy bay:      
  ![Đặt WP khởi đầu và mode bay](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/set-mode-wp.png?raw=true)
  - Arm máy bay để bắt đầu quá trình bay tự động:
  ![Arm](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/arm.png?raw=true)
  - Đặt WP tiếp theo thành WP số 9 để hạ cánh:
  ![Hạ cánh](https://github.com/binhnt94/ardupilot/blob/master/tutorial-images/wp-land.png?raw=true)
---
 ### 6. Tham số cấu hình cho Autopilot:
  - Tham số điều khiển bay mô phỏng cho QuadPlane: ${workspaceFolder}/X-Plane configuration/xplane_sil.param
  - Nhiệm vụ bay 916 Hoa Lac: 916_15012020.waypoints      
  - Tất cả nằm trong đường dẫn "/X-Plane configuration" của project.
---
# Tutorial for QuadPlane Simulation
An Ardupilot control model for QuadPlane flight simulation with X-Plane

## 1. Overview
This project provide a collection of useful resources for beginners to understand control algorithms for an QuadPlane.
The project has come with real-time UDP protocol for controlling aircraft model in X-Plane.

## 2. Getting started
  * Install and purchase an X-Plane according to https://www.evernote.com/shard/s659/sh/4bfff893-1356-9ed0-3da8-be3b00f1a5a9/f106fd834ee6499e70ace57bcb7f8911

## 3. Flight your own models and learn.
  * Refer [modelling instruction](https://developer.x-plane.com/manuals/planemaker/#The_Plane_Maker_Interface) from Laminar Research
  to build your own aircraft models.   