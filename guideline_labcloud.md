# Guideline lab Cloud

## 1. Dựng Lab Devstack branch stable/train. Môi trường: Ubuntu 18.04. 

### Bước 1: Tải về bộ cài training git. Sử dụng lệnh:  

git clone https://git.openstack.org/openstack/training-labs.git

### Bước 2: Tạo folder img bên trong training-labs/labs/ bằng cách sử dụng lệnh:
mkdir -p training-labs/labs/img

### Bước 3: Di chuyển đến thư mục training-labs/lab, để tiến hành buid, sử dụng lệnh:
cd training-labs/labs
./st.py -b cluster

### Bước 4: Tiến hành build. Code sẽ kiểm tra bên trong thư mục img có file iso chưa, nếu chưa có thì sẽ tiến hành download ubuntu server 18.04.

### Bước 5: Sau khi download hoàn tất, code sẽ đến phần cài đặt 1 node controller và 1 node compute trên virtual box.

### Bước 6: Cài đặt hoàn tất. Mở trình duyệt vào địa chỉ:
http://127.0.0.1:8888/horizon/

### Bước 7: Đăng nhập:
Domain: default
User Name: admin 
Password: admin_user_secret

### Bước 8: Đăng nhập thành công


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

### Bước 4: Tạo instance:

Project > Compute > Instances > Launch Instance

Ở Details, thiết lập các giá trị:
Instace Name: test
Count: 1

Sau đó chọn Next.

Ở Source, thiết lập các giá trị:
Select Boot Source: Image
Create New Volume: No
Allocated: Xenial Ubuntu

Sau đó chọn Next

Ở Flavor, chọn t2.micro sau đó chọn Key Pair.

Ở Key Pair, chọn Create Key Pair sau đó thiết lập
Key Pair Name: hungcao
Key Type: X509 Certificate

Sau đó chọn Create Keypair và lưu lại private key.

Chọn Launch Instance.

### Bước 5: Sử dụng instance:

Đợi instance khởi động xong, chọn vào tên instance sau đó chuyển qua tab Console để sử dụng instance.
Nếu không nhận phản hồi từ bàn phím thì chọn Click here to show only console.


