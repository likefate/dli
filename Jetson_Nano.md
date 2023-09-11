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
