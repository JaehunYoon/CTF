# Wireshark

## Problem

와이어샤크..? 그게 뭐지??

***

## Solution

문제의 `Download` 버튼을 누르면 `CTF_network_Lapio.pcapng` 라는 파일이 저장된다.

이 파일을 Wireshark를 통해 열어보면 패킷 정보들이 나열되는데, 필터 기능을 통해 `http`로 필터링한 후 String 형식으로 `lapio`를 검색해보면 다음과 같이 html 패킷과 png 패킷이 나온다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Network/Wireshark/Image/wireshark.PNG)

이 중 PNG 파일이 `Response`된 패킷에서 Export Packet Bytes를 이용하여 바이너리 파일을 `PNG` 형식으로 추출하면 다음과 같이 `Flag`가 포함된 그림을 볼 수 있다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Network/Wireshark/Image/flag.PNG)

Flag : **DISC{H3lp_m3@@!!}**