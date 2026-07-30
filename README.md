# Dev Workstation Setup

이 저장소는 개발 워크스테이션 구축 미션 결과물입니다.
터미널, Docker(OrbStack), Git/GitHub 환경을 세팅하고 검증합니다.

## 진행 상황
- [ ] 터미널 작업 디렉토리 설정
- [ ] Docker 설치 확인
- [ ] Dockerfile 작성 및 웹 서버 컨테이너화
- [ ] Git/GitHub 연동
      
## 터미널 조작 로그
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

## 권한 실습
### 파일 권한 변경
- 변경 전: -rw-r--r--
- 명령: chmod 644 perm_test.txt
- 변경 후: -rw-r--r--

### 디렉토리 권한 변경
- 변경 전: drwxr-xr-x
- 명령: chmod 755 perm_dir
- 변경 후: drwxr-xr-x

## Docker 설치 점검
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

## Docker 기본 운영 명령
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

## 컨테이너 종료 vs 유지 차이 관찰
- `docker run -it ubuntu bash` 후 `exit` 하면 → 컨테이너가 즉시 종료됨 (Exited 상태)
- `docker run -d ubuntu sleep 1000` → 백그라운드에서 계속 실행 유지됨 (Up 상태)
- `docker exec -it <id> bash` → 이미 "실행 중인" 컨테이너 안에 추가로 접속하는 것. exec 세션에서 exit해도 컨테이너 자체는 계속 살아있음 (원래 실행 중이던 sleep 1000 프로세스가 안 죽었으니까)
