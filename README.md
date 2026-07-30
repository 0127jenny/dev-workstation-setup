# Dev Workstation Setup

## 프로젝트 개요
터미널, Docker(OrbStack), Git/GitHub을 활용해 재현 가능한 개발 워크스테이션을 구축하고,
간단한 웹 서버를 Dockerfile로 컨테이너화하여 포트 매핑 및 볼륨 영속성을 검증한 미션.

## 실행 환경
- OS: macOS Sequoia version 15.7.4
- 터미널: VSCode 내장 터미널 (zsh)
- Docker: Docker version 28.5.2
- Git: git version 2.53.0

## 터미널 조작 로그 기록 (요구사항 2)
아래 명령어로 디렉토리/파일 생성, 복사, 이동, 삭제를 수행함.

\`\`\`
c0127jenny8859@c3r3s7 dev-workstation-mission % pwd
/Users/c0127jenny8859/Desktop/dev-workstation-mission
c0127jenny8859@c3r3s7 dev-workstation-mission % ls -al
total 0
drwxr-xr-x  2 c0127jenny8859  c0127jenny8859   64 Jul 30 15:19 .
drwx------+ 6 c0127jenny8859  c0127jenny8859  192 Jul 30 15:19 ..
c0127jenny8859@c3r3s7 dev-workstation-mission % mkdir practice
c0127jenny8859@c3r3s7 dev-workstation-mission % cd practice
c0127jenny8859@c3r3s7 practice % cd ~/Desktop
c0127jenny8859@c3r3s7 Desktop % cd ~/Desktop
c0127jenny8859@c3r3s7 Desktop % mkdir dev-workstation-mission
mkdir: dev-workstation-mission: File exists
c0127jenny8859@c3r3s7 Desktop % mkdir dev-workstation-mission
c0127jenny8859@c3r3s7 Desktop % cd dev-workstation-mission
c0127jenny8859@c3r3s7 dev-workstation-mission % pwd
/Users/c0127jenny8859/Desktop/dev-workstation-mission
c0127jenny8859@c3r3s7 dev-workstation-mission % pwd
/Users/c0127jenny8859/Desktop/dev-workstation-mission
c0127jenny8859@c3r3s7 dev-workstation-mission % ls -al
total 0
drwxr-xr-x  2 c0127jenny8859  c0127jenny8859   64 Jul 30 15:25 .
drwx------+ 5 c0127jenny8859  c0127jenny8859  160 Jul 30 15:25 ..
c0127jenny8859@c3r3s7 dev-workstation-mission % mkdir practice
c0127jenny8859@c3r3s7 dev-workstation-mission % cd practice
c0127jenny8859@c3r3s7 practice % touch test.txt
c0127jenny8859@c3r3s7 practice % echo "hello" > test.txt
c0127jenny8859@c3r3s7 practice % cat test.txt
hello
c0127jenny8859@c3r3s7 practice % cp test.txt test_copy.txt
c0127jenny8859@c3r3s7 practice % mv test_copy.txt renamed.txt
c0127jenny8859@c3r3s7 practice % ls -al
total 32
drwxr-xr-x  5 c0127jenny8859  c0127jenny8859   160 Jul 30 15:29 .
drwxr-xr-x  4 c0127jenny8859  c0127jenny8859   128 Jul 30 15:29 ..
-rw-r--r--@ 1 c0127jenny8859  c0127jenny8859  6148 Jul 30 15:29 .DS_Store
-rw-r--r--@ 1 c0127jenny8859  c0127jenny8859     6 Jul 30 15:29 renamed.txt
-rw-r--r--@ 1 c0127jenny8859  c0127jenny8859     6 Jul 30 15:28 test.txt
c0127jenny8859@c3r3s7 practice % rm renamed.txt
c0127jenny8859@c3r3s7 practice % cd ..
c0127jenny8859@c3r3s7 dev-workstation-mission % 
![Uploading 스크린샷 2026-07-30 오후 3.31.56.png…]()
<img width="975" height="949" alt="스크린샷 2026-07-30 오후 3 31 04" src="https://github.com/user-attachments/assets/6914063e-25ff-4547-9d64-9f9b8afd3420" />
<img width="948" height="467" alt="스크린샷 2026-07-30 오후 3 30 16" src="https://github.com/user-attachments/assets/3115289a-80c5-4048-ab8b-f1d03b576152" />

## 권한 실습 및 증거 기록 (요구사항 3)
### 파일 권한 변경
- 변경 전: -rw-r--r--
- 명령: chmod 644 perm_test.txt
- 변경 후: -rw-r--r--

### 디렉토리 권한 변경
- 변경 전: drwxr-xr-x
- 명령: chmod 755 perm_dir
- 변경 후: drwxr-xr-x

## Docker 설치 및 기본 점검 (요구사항 4)
$ docker --version
Docker version 28.5.2, build ecc6942

$ docker info
Client:
 Version:    28.5.2
 Context:    orbstack
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.29.1
    Path:     /Users/c0127jenny8859/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.40.3
    Path:     /Users/c0127jenny8859/.docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 28.5.2
 Storage Driver: overlay2
  Backing Filesystem: btrfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1c4457e00facac03ce1d75f7b6777a7a851e5c41
 runc version: d842d7719497cc3b774fd71620278ac9e17710e0
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.17.8-orbstack-00308-g8f9c941121b1
 Operating System: OrbStack
 OSType: linux
 Architecture: x86_64
 CPUs: 6
 Total Memory: 15.67GiB
 Name: orbstack
 ID: 02f25a1c-d336-46a9-82fe-8e3fb92fc23d
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine
 Default Address Pools:
   Base: 192.168.97.0/24, Size: 24
   Base: 192.168.107.0/24, Size: 24
   Base: 192.168.117.0/24, Size: 24
   Base: 192.168.147.0/24, Size: 24
   Base: 192.168.148.0/24, Size: 24
   Base: 192.168.155.0/24, Size: 24
   Base: 192.168.156.0/24, Size: 24
   Base: 192.168.158.0/24, Size: 24
   Base: 192.168.163.0/24, Size: 24
   Base: 192.168.164.0/24, Size: 24
   Base: 192.168.165.0/24, Size: 24
   Base: 192.168.166.0/24, Size: 24
   Base: 192.168.167.0/24, Size: 24
   Base: 192.168.171.0/24, Size: 24
   Base: 192.168.172.0/24, Size: 24
   Base: 192.168.181.0/24, Size: 24
   Base: 192.168.183.0/24, Size: 24
   Base: 192.168.186.0/24, Size: 24
   Base: 192.168.207.0/24, Size: 24
   Base: 192.168.214.0/24, Size: 24
   Base: 192.168.215.0/24, Size: 24
   Base: 192.168.216.0/24, Size: 24
   Base: 192.168.223.0/24, Size: 24
   Base: 192.168.227.0/24, Size: 24
   Base: 192.168.228.0/24, Size: 24
   Base: 192.168.229.0/24, Size: 24
   Base: 192.168.237.0/24, Size: 24
   Base: 192.168.239.0/24, Size: 24
   Base: 192.168.242.0/24, Size: 24
   Base: 192.168.247.0/24, Size: 24
   Base: fd07:b51a:cc66:d000::/56, Size: 64

WARNING: DOCKER_INSECURE_NO_IPTABLES_RAW is set

$ git --version
git version 2.53.0

## Docker 기본 운영 명령 수행 (요구사항 5)
$ docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:c3cbe1cc1aa588a64951ac6286e0df7b27fe2e6324b1001c619bb358770c0178
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest

$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
hello-world   latest    e2ac70e7319a   4 months ago   10.1kB

$ docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
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

$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

$ docker logs 6ed77b040509
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
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

$ docker stats --no-stream
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT   MEM %     NET I/O   BLOCK I/O   PIDS

## 컨테이너 실행 연습 (요구사항 6) (컨테이너 종료 vs 유지 차이 관찰)
- `docker run -it ubuntu bash` 후 `exit` 하면 → 컨테이너가 즉시 종료됨 (Exited 상태)
- `docker run -d ubuntu sleep 1000` → 백그라운드에서 계속 실행 유지됨 (Up 상태)
- `docker exec -it <id> bash` → 이미 "실행 중인" 컨테이너 안에 추가로 접속하는 것. exec 세션에서 exit해도 컨테이너 자체는 계속 살아있음 (원래 실행 중이던 sleep 1000 프로세스가 안 죽었으니까)

## 기존 Dockerfile 기반 커스텀 이미지 제작 (요구사항 7-A)

### 선택한 베이스 이미지
- nginx:latest (공식 NGINX 이미지)

### 커스텀 포인트
- `COPY site/ /usr/share/nginx/html/` → 기본 NGINX 환영 페이지 대신, 직접 만든 index.html을 서빙하도록 교체함

### Dockerfile 내용
\`\`\`dockerfile
FROM nginx:latest
COPY site/ /usr/share/nginx/html/
EXPOSE 80
\`\`\`

### 빌드/실행 명령 + 결과
\`\`\`
$ docker build -t my-custom-nginx .
[+] Building 8.5s (7/7) FINISHED                          docker:orbstack
 => [internal] load build definition from Dockerfile                 0.1s
 => => transferring dockerfile: 98B                                  0.0s
 => [internal] load metadata for docker.io/library/nginx:latest      3.1s
 => [internal] load .dockerignore                                    0.2s
 => => transferring context: 2B                                      0.0s
 => [internal] load build context                                    0.2s
 => => transferring context: 116B                                    0.0s
 => [1/2] FROM docker.io/library/nginx:latest@sha256:5a88c9c4547944  4.2s
 => => resolve docker.io/library/nginx:latest@sha256:5a88c9c4547944  0.2s
 => => sha256:db4f612f385437d11eb26620a4f1d7efb3ff4 2.29kB / 2.29kB  0.0s
 => => sha256:4e5db4761e0ff445f7fd29aad680ad28e8abf 9.09kB / 9.09kB  0.0s
 => => sha256:5a88c9c45479443d7be2eadc894b4ed0a98 10.23kB / 10.23kB  0.0s
 => => sha256:062e450697faa5f02a3a74eba9864ee4d79 29.78MB / 29.78MB  0.8s
 => => sha256:82454cdbf456a77f9ff1bb88b121c2a739e 33.33MB / 33.33MB  1.5s
 => => sha256:3c7ab7949321f47c96fc0918f9f72e8f51bd452cd 626B / 626B  0.7s
 => => sha256:cacfcdd01f309c65d69372716e799ea741065ac1b 955B / 955B  1.0s
 => => sha256:b6698f04e005497a7f495c0719358d43890cb3997 403B / 403B  1.1s
 => => extracting sha256:062e450697faa5f02a3a74eba9864ee4d79bc9cfbd  1.1s
 => => sha256:2bedaf25031a24fb70b9dc2d56cb17139186d 1.21kB / 1.21kB  1.3s
 => => sha256:d26f27cc8c41e321394cb3c9a80915d90d5f1 1.40kB / 1.40kB  1.8s
 => => extracting sha256:82454cdbf456a77f9ff1bb88b121c2a739e38c30ea  0.7s
 => => extracting sha256:3c7ab7949321f47c96fc0918f9f72e8f51bd452cde  0.0s
 => => extracting sha256:cacfcdd01f309c65d69372716e799ea741065ac1b1  0.0s
 => => extracting sha256:b6698f04e005497a7f495c0719358d43890cb3997a  0.0s
 => => extracting sha256:2bedaf25031a24fb70b9dc2d56cb17139186d1ae5f  0.0s
 => => extracting sha256:d26f27cc8c41e321394cb3c9a80915d90d5f1f1d3c  0.0s
 => [2/2] COPY site/ /usr/share/nginx/html/                          0.4s
 => exporting to image                                               0.2s
 => => exporting layers                                              0.1s
 => => writing image sha256:4254ccebb3d95c1fb8b50f633ddff6913fc0d6f  0.0s
 => => naming to docker.io/library/my-custom-nginx  

$ docker run -d -p 8080:80 --name my-nginx-container my-custom-nginx
870caeafc048eeba393a7dc370698a48e16323f2d52bdb153a4394ace07390b3

$ docker ps
CONTAINER ID   IMAGE             COMMAND                  CREATED          STATUS          PORTS                                     NAMES
870caeafc048   my-custom-nginx   "/docker-entrypoint.…"   24 seconds ago   Up 24 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-nginx-container
\`\`\`

## 포트 매핑 및 접속 증거 (요구사항 8)
<img width="2560" height="1440" alt="스크린샷 2026-07-30 오후 4 46 57" src="https://github.com/user-attachments/assets/4e4d75af-5e4e-46b5-9a5c-82f58633b1a7" />


## Docker 볼륨 영속성 검증 (요구사항 9)

\`\`\`
$ docker volume create mydata
mydata

$ docker run -d -v mydata:/data --name volume-test ubuntu sleep 1000
ce92a2434047

$ docker exec volume-test sh -c "echo 'persisted data' > /data/test.txt"

$ docker exec volume-test cat /data/test.txt
persisted data

$ docker rm -f volume-test
volume-test

$ docker run --rm -v mydata:/data ubuntu cat /data/test.txt
persisted data
\`\`\`

### 결론
`volume-test` 컨테이너를 완전히 삭제(`docker rm -f`)한 후에도, 같은 볼륨(`mydata`)을 연결한 새 컨테이너에서 파일을 읽을 수 있었음. 이는 데이터가 컨테이너가 아니라 볼륨에 저장되어, 컨테이너 삭제와 무관하게 유지됨을 증명함.

## Git 설정 및 GitHub 연동 (요구사항 10)

### Git 설정 확인
\`\`\`
$ git config --list
credential.helper=osxkeychain
user.name=채지연
user.email=“0127jenny@gmail.com”
init.defaultbranch=main
\`\`\`

### GitHub 연동 증거
<img width="1227" height="893" alt="스크린샷 2026-07-30 오후 5 03 27" src="https://github.com/user-attachments/assets/b1a48202-1348-4c65-918a-8ba59cd6759b" />
<img width="1224" height="821" alt="스크린샷 2026-07-30 오후 5 02 57" src="https://github.com/user-attachments/assets/b60086a9-fa50-4d40-a633-a4ada32c004e" />

## 트러블슈팅

### 사례 1
- 문제: docker build 시 "unable to prepare context" 에러 발생
- 원인 가설: 터미널이 Dockerfile이 있는 폴더가 아닌 다른 위치에 있었음
- 확인: `pwd`로 현재 위치 확인해보니 다른 폴더였음
- 해결: `cd ~/Desktop/dev-workstation-mission`으로 이동 후 재시도하여 해결
