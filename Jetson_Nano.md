# 젯슨 나노 세팅

1. sd포맷터로 sd카드 포맷
2. etcher 와 sd카드 이미지 다운로드 후 sd카드 굽기
3. 젯슨 나노에 키보드, 마우스 등을 연결
![image](https://github.com/server-123/Zetson_Nano/assets/73692229/960b1275-9df1-425c-b149-f210ef662777)
![image](https://github.com/server-123/Zetson_Nano/assets/73692229/2b813228-5a89-412f-a9c2-1eb09b371f78)
4. 젯슨 나노 부팅 후 설정 완료

# 쿨링 팬 연결

아래 명령어 Terminal에서 차례대로 실행 ( 업데이트, 젯슨 나노의 상태 확인 소프트웨어 ) 설치
~~~shell
sudo apt-get upgrade
sudo apt-get update
sudo apt install python3-pip
sudo -H pip3 install -U jetson-stats
reboot #재부팅
jtop #젯슨 나노 상태창 열기
~~~

쿨링팬 연결
이후 아래 명령어 실행
~~~shell
cd Downloads
git clone https://github.com/jetsonworld/jetson-fan-ctl.git
cd jetson-fan-ctl
sudo sh install.sh
~~~

# CSI 카메라 연결
CSI 카메라 연결 후에 아래 명령어 실행
~~~shell
git clone https://github.com/jetsonhacks/CSI-Camera.git
cd CSI-Camera
python3 simple_camera.py
~~~

# SSH 연결
~~~shell
cd ..
cd ..
ssh dli@192.168.55.1
dli
~~~
위 명령어 실행 시 Jetson nano와 연결됨.

# Docker 설치
~~~shell
mkdir -p ~/nvdli-data # 디렉토리 추가
echo "sudo docker run --runtime nvidia -it --rm --network host \
    --volume ~/nvdli-data:/nvdli-nano/data \
    --volume /tmp/argus_socket:/tmp/argus_socket \
    --device /dev/video0 \
    nvcr.io/nvidia/dli/dli-nano-ai:v2.0.2-r32.7.1kr" > docker_dli_run.sh # 실행 파일 생성
chmod +x docker_dli_run.sh # 파일 권한 부여
./docker_dli_run.sh
~~~

192.168.55.1 접속
이후 로그인하면 JupyterLab에 들어가짐

# Classification
1. 주피터랩을 실행한다.
2. classification 폴더의 classification_interactive.ipynb에 있는 코드들을 순서대로 실행한다.
3. 엄지를 위로 올린 사진과 아래로 내린 사진 여러 장을 학습시킨다.

# Regression
1. 주피터랩을 실행한다.
2. regression 폴더의 regression_interactive.ipynb에 있는 코드들을 순서대로 실행한다.
3. 얼굴 사진을 여러 장 찍은 뒤 에포크 값을 조정하고 학습시킨다.
