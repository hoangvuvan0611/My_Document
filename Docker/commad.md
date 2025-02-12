***Lệnh cơ bản và thông tin về hệ thống
- docker version 
-> Hiển thị phiên bản docker client và docker daemon (Engine)

- docker info 
-> Hiển thị thông tin chi tiết về hệ thống docker: Số lượng container, image, driver lưu trữ, plugin...

- docker help
-> Danh sách các lệnh có sẵn: `docker [command] --help` để xem những hướng dẫn cụ thể cho từng lệnh

***Quản lý container
- docker run
-> Khởi tạo và chạy một container từ docker images
    `-d`: chạy container ở chế độ nền
    `-it`: chế độ tương tác (interactive + tty)
    `-p HOST_PORT:CONTAINER_PORT`: ánh xạ cổng từ host sang container
    `--name`: đặt tên cho container
vd: docker run -d -p 8080:80 --name [name for container] [docker name image] 

- docker create
-> Tạo một docker container từ docker image nhưng không khởi động ngay, dùng khi muốn cấu hình thêm sau rồi mới khởi động
vd: docker create --name [name for container] [docker name image]

- docker start
-> Khởi động container đã được tạo hoặc đang dừng
vd: docker start [docker container name]

- docker stop
-> Dừng container đang run
vd: docker stop [docker container name]

- docker restart
-> Khởi động lại container
vd: docker restart [docker container name]

- docker kill 
-> Buộc dừng container ngay lập tức (force - không chờ timeout)
vd: docker kill [docker container name]

- docker rm
-> Xóa một hoặc nhiều container đã dừng
vd: docker rm [docker container name]

- docker ps
-> Liệt kê danh sách container
-> Mặc định chỉ hiển thị danh sách container đang chạy
-> -a hoặc --all liệt kê tất cả các container
vd: docker ps -a

- docker exec
-> Chạy lệnh bên trong một container đang chạy, thường dùng để mở shell trong container 
vd: docker exec -it [docker_container_name] /bin/bash 

- docker attach
-> Kết nối (attach) vào container đang chạy để xem đầu ra hoặc tương tác trực tiếp
vd: docker attach [docker_container_name]

- docker logs --follow [docker_container_name]
-> hiển thị log của container

- docker inspect [docker_container_name]
-> Trả về thông tin chi tiết (JSON) của container (hoặc image, network...)

- docker cp 
-> Sao chép file hoặc thư mục giữa container và host 
vd: docker cp [docker_container_name]:/path/to/file /local/path
vd: docker cp /local/path [docker_container_name]:/path/to/dest 

- docker rename
-> Đổi tên một container đã tồn tại
vd: docker rename old_name new_name

- docker update
-> Cập nhật các cài đặt (tài nguyên, restart policy) của container đang chạy 
vd: docker update --restart=no [docker_container_name] 

- docker stats 
-> Hiển thị thống kê tài nguyên sử dụng (CPU, memory, network,...) của container đang chạy



*** Quản lý images
- docker build 
-> Xây dựng một image từ dockerfile và context 
vd: docker build -t [docker_image_name]

- docker pull 
-> Tải image từ docker hub hoặc registry khác về máy cục bộ 
vd: docker pull [docker_image_name]:[version]

- docker push 
-> Đẩy image từ máy cục bộ lên registry (vd: docker hub) 
vd: docker push username/[docker_image_name]:[version]

- docker images (hoặc docker image ls)
-> Liệt kê image có trên máy local 

- docker rmi 
-> Xóa một hoặc nhiều image khỏi máy cục bộ 
vd: docker rmi [docker_image_name]

- docker tag 
-> Gán tag mới cho image, hữu ích khi bạn cần đổi tên hoặc chuẩn bị đẩy lên registry
vd: docker tag [docker_image_tag] username/[docker_image_name]:[version]

- docker commit 
-> Tạo một image mới từ những thay đổi trong container 
vd: docker commit [docker_container_name] [new_docker_image_name]

- docker save 
-> Lưu image thành một file tar để sao lưu hoặc chuyển giao 
vd: docker save -o [docker_image_name].tar [docker_image_name]

- docker load 
-> Tải image từ file tar đã lưu trước đó 
vd: docker load -i [docker_image_name].tar 



*** Quản lý network
- docker network create
-> Docker cho phép tạo và quản lý các network để các container giao tiếp với nhau một cách linh hoạt
vd: docker network create [my_network]

- docker network ls
-> Liệt kê các network có trên hệ thống

- docker network inspect 
-> Xem thông tin chi tiết của một network
vd: docker network inspect my-network 

- docker network connect 
-> Kết nối một container vào một network đã tạo
vd: docker network connect [my_network] [my_container]

