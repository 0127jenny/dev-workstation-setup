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
