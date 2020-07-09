# Guideline lab Cloud

## 1. Dựng Lab Devstack branch stable/train. Môi trường: Ubuntu 18.04. 

### Bước 1: Tải về bộ cài training git. Sử dụng lệnh:  

git clone https://git.openstack.org/openstack/training-labs.git

![photo_2020-07-09_16-51-04](https://user-images.githubusercontent.com/41882267/87026630-34d22100-c206-11ea-8b4c-62b6e7722a80.jpg)


### Bước 2: Tạo folder img bên trong training-labs/labs/ bằng cách sử dụng lệnh:
mkdir -p training-labs/labs/img

### Bước 3: Di chuyển đến thư mục training-labs/lab, để tiến hành buid, sử dụng lệnh:
cd training-labs/labs
./st.py -b cluster

![photo_2020-07-09_16-50-51](https://user-images.githubusercontent.com/41882267/87026693-49161e00-c206-11ea-8516-4e46ef0b9cbf.jpg)


### Bước 4: Tiến hành build. Code sẽ kiểm tra bên trong thư mục img có file iso chưa, nếu chưa có thì sẽ tiến hành download ubuntu server 18.04.

### Bước 5: Sau khi download hoàn tất, code sẽ đến phần cài đặt 1 node controller và 1 node compute trên virtual box.

![photo_2020-07-09_16-51-08](https://user-images.githubusercontent.com/41882267/87026761-6814b000-c206-11ea-8927-0777026112cd.jpg)


### Bước 6: Cài đặt hoàn tất. Mở trình duyệt vào địa chỉ:
http://127.0.0.1:8888/horizon/

### Bước 7: Đăng nhập:
Domain: default
User Name: admin 
Password: admin_user_secret
![image](https://user-images.githubusercontent.com/41882267/87026980-b164ff80-c206-11ea-8e24-880a59440119.png)

### Bước 8: Đăng nhập thành công

![image](https://user-images.githubusercontent.com/41882267/87027106-dce7ea00-c206-11ea-86a2-9e6c391ad3bd.png)


## 2. Dựng 1 VM trên DevStack chạy Gitlab CE, tạo repo và demo các thao tác quản lý source code (commit, push, pull)

### Bước 1: Chọn Ubuntu Xenial làm hệ điều hành. Download xenial-server-cloudimg-arm64-disk1.img từ địa chỉ:
https://cloud-images.ubuntu.com/xenial/20200625/

### Bước 2: Tạo image từ horizon. 
Admin > Compute > Images > Create Image

Thiết lập các giá trị sau:
Image Name: Xenial Ubuntu
File: xenial-server-cloudimg-arm64-disk1.img
Format: QCOW2 - QEMU Emulator

Sau đó chọn Create Image

![photo_2020-07-09_16-51-10](https://user-images.githubusercontent.com/41882267/87027175-fb4de580-c206-11ea-84a8-f4443c01807b.jpg)


### Bước 3: Tạo flavor:
Admin > Compute > Flavors > Create Flavor

Thiết lập các giá trị sau:
Name: t2.micro
VCPUs: 1
RAM (MB): 512
Root Disk (GB): 5
Ephemeral Disk (GB): 1
Swap Disk (MB): 1024
RX/TX Factor: 1

Sau đó chọn Create Flavor

![photo_2020-07-09_16-51-13](https://user-images.githubusercontent.com/41882267/87027205-07d23e00-c207-11ea-9cf7-f233807a83a1.jpg)


### Bước 4: Tạo instance:

Project > Compute > Instances > Launch Instance

Ở Details, thiết lập các giá trị:
Instace Name: test
Count: 1

Sau đó chọn Next.
![photo_2020-07-09_16-51-16](https://user-images.githubusercontent.com/41882267/87027270-1fa9c200-c207-11ea-8e6e-e56400ba6eab.jpg)


Ở Source, thiết lập các giá trị:
Select Boot Source: Image
Create New Volume: No
Allocated: Xenial Ubuntu

Sau đó chọn Next

![photo_2020-07-09_16-51-18](https://user-images.githubusercontent.com/41882267/87027296-2b958400-c207-11ea-9b3c-eb301aefb31a.jpg)


Ở Flavor, chọn t2.micro sau đó chọn Key Pair.

![photo_2020-07-09_16-51-20](https://user-images.githubusercontent.com/41882267/87027328-394b0980-c207-11ea-8e2c-db4520db1a34.jpg)


Ở Key Pair, chọn Create Key Pair sau đó thiết lập
Key Pair Name: hungcao
Key Type: X509 Certificate

Sau đó chọn Create Keypair và lưu lại private key.

![photo_2020-07-09_16-51-26](https://user-images.githubusercontent.com/41882267/87027384-49fb7f80-c207-11ea-9359-18e68352927f.jpg)


Chọn Done sau đó chọn Launch Instance.

### Bước 5: Sử dụng instance:

Đợi instance khởi động xong, chọn vào tên instance sau đó chuyển qua tab Console để sử dụng instance.
Nếu không nhận phản hồi từ bàn phím thì chọn Click here to show only console.

![photo_2020-07-09_16-51-31](https://user-images.githubusercontent.com/41882267/87027505-744d3d00-c207-11ea-94a7-2db533eb2e83.jpg)


