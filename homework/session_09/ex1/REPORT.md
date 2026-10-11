# Báo Cáo Thực Hành: Kiểm tra cài đặt Docker Engine và chạy Container Hello-World

- **Môn học / Khóa học:** IT209
- **Bài thực hành:** Session 09 - Bài 1: Kiểm tra cài đặt Docker Engine và chạy Container Hello-World
- **Người thực hiện:** Hồ Khánh Linh

---

## 1. Mục tiêu
- Thực hành chạy các lệnh kiểm tra phiên bản Docker CLI.
- Kiểm tra kết nối tới Docker Daemon mà không cần quyền sudo / kiểm tra trạng thái Docker Engine.
- Khởi chạy container đầu tiên (`hello-world`) trên máy cá nhân và xác minh hệ thống hoạt động chính xác.

---

## 2. Kết quả thực hiện các lệnh CLI

### Lệnh 1: `docker version`
Kiểm tra chi tiết phiên bản của Docker Client và Docker Server/Engine:

```bash
$ docker version
Client:
 Version:           29.8.2
 API version:       1.56
 Go version:        go1.26.8
 Git commit:        7fc2dff
 Built:             Wed Sep 30 19:32:03 2026
 OS/Arch:           darwin/arm64
 Context:           desktop-linux

Server: Docker Desktop 4.94.0 (241994)
 Engine:
  Version:          29.8.2
  API version:      1.56 (minimum version 1.40)
  Go version:       go1.26.8
  Git commit:       8af9fe3
  Built:            Wed Sep 30 19:31:50 2026
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          v2.3.6
  GitCommit:        ee2735368117d2eb259779949d5e75cdafec9761
 runc:
  Version:          1.5.1
  GitCommit:        v1.5.1-0-g8f2685a4
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

---

### Lệnh 2: `docker info`
Kiểm tra cấu hình chi tiết, thông tin phần cứng, driver, containers, images và hệ điều hành của Docker:

```bash
$ docker info
Client:
 Version:    29.8.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.144.0
    Path:     /Users/khanhly/.docker/cli-plugins/docker-agent
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.31.0
    Path:     /Users/khanhly/.docker/cli-plugins/docker-ai
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.37.2
    Path:     /Users/khanhly/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v5.5.1
    Path:     /Users/khanhly/.docker/cli-plugins/docker-compose
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.0.47
    Path:     /Users/khanhly/.docker/cli-plugins/docker-debug
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  v0.4.4
    Path:     /Users/khanhly/.docker/cli-plugins/docker-desktop
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.7
    Path:     /Users/khanhly/.docker/cli-plugins/docker-dhi
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.31
    Path:     /Users/khanhly/.docker/cli-plugins/docker-extension
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.0
    Path:     /Users/khanhly/.docker/cli-plugins/docker-init
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.1
    Path:     /Users/khanhly/.docker/cli-plugins/docker-mcp
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.6
    Path:     /Users/khanhly/.docker/cli-plugins/docker-model
  offload: Docker Offload (Docker Inc.)
    Version:  v0.6.53
    Path:     /Users/khanhly/.docker/cli-plugins/docker-offload
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.2.4
    Path:     /Users/khanhly/.docker/cli-plugins/docker-pass
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     /Users/khanhly/.docker/cli-plugins/docker-sandbox
  scout: Docker Scout (Docker Inc.)
    Version:  v1.25.0
    Path:     /Users/khanhly/.docker/cli-plugins/docker-scout

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 2
 Server Version: 29.8.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: ee2735368117d2eb259779949d5e75cdafec9761
 runc version: v1.5.1-0-g8f2685a4
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 7.0.14-linuxkit
 Operating System: Docker Desktop
 OSType: linux
 Architecture: aarch64
 CPUs: 8
 Total Memory: 3.825GiB
 Name: docker-desktop
 ID: 39d55020-cb4f-4ccb-9851-7ef22df4501c
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=unix:///Users/khanhly/Library/Containers/com.docker.docker/Data/docker-cli.sock
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
```

---

### Lệnh 3: `docker run hello-world`
Tải image `hello-world` từ Docker Hub và khởi chạy container đầu tiên:

```bash
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world

58dee6a49ef1: Pulling fs layer 58dee6a49ef1: Download complete 58dee6a49ef1: Extracting 1 s58dee6a49ef1: Pull complete 
c3bdf82c34d1: Download complete Digest: sha256:5e23090353324d887c48ad5e5c56d294eab81588df9605b07d1afe895f9cc8f8
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm64v8)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

---

## 3. Đánh giá và Kết luận
- Lệnh `docker run hello-world` đã chạy thành công và xuất hiện thông báo:
  > **“Hello from Docker! This message shows that your installation appears to be working correctly.”**
- Docker Daemon đã kết nối và giao tiếp ổn định với Docker CLI mà không gặp lỗi phân quyền hay lỗi socket.
- Hệ thống Docker đã sẵn sàng để phục vụ các bài thực hành và dự án tiếp theo.
