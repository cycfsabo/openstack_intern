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


