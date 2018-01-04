# Gold Dog

## Problem

2018년의 띠는 황금개띠다. 
이를 기념하여 동아리 Lapio의 부장 K 군은 동아리원 S 양에게 황금개 그림을 그려달라고 외주를 맡겼다. 
3일간 공을 들여 그리기 작업을 마친 S 양은 K 군에게 그림을 제출하려고 하였으나 의문의 괴한 J 군에게 암살당하였고, 
괴한 J 군은 자신의 흔적을 남기는 사이코패스여서, 해당 그림에 자신의 메시지를 남겨두었다. 
수사관인 당신은 J 군의 메시지를 찾아야한다. 

J 군의 메시지로 확인되는 것을 찾은 후, 해당 메시지를 DISC{메시지} 형식으로 플래그에 등록하라. 

HINT : 메모장으로 열어도 나올 것 같은데..?

***

## Solution

문제의 Download 버튼을 누르면 다음과 같은 `Forensic100_Gold_Dog.png` 파일이 저장된다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Forensic/Gold%20Dog/Image/Forensic100_Gold_Dog.png)

문제의 힌트에는 "메모장으로 열어도 나올 것 같은데..?" 라고 되어 있었기 때문에 PNG 파일을 메모장으로 열어보았다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Forensic/Gold%20Dog/Image/notepad.PNG)

파일의 끝 부분으로 가보니 다음과 같이 유일하게 읽을 만 하게 생긴 문자열이 존재했다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Forensic/Gold%20Dog/Image/flag.PNG)

FLAG : **DISC{PNG_FI13_F0rmat!!}**