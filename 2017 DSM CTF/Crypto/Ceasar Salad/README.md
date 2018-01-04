# Ceasar Salad

## Problem

카이사르 암호(Caesar cipher) 또는 시저 암호는 암호학에서 다루는 간단한 치환암호의 일종이다. 암호화하고자 하는 내용을 알파벳별로 일정한 거리만큼 밀어서 다른 알파벳으로 치환하는 방식이다. 
예를 들어 3글자씩 밀어내는 카이사르 암호로 'COME TO ROME'을 암호화하면 'FRPH WR URPH'가 된다. 
Ceasar 암호로 암호화된 문장을 복호화해 Flag를 찾자!

***

## Solution

문제의 Download 버튼을 누르면 다음과 같은 `encrypted.txt` 파일이 저장된다.

![Image](Image_Link.PNG)

텍스트 파일을 보니 시저 암호를 이용하여 치환된 것으로 보인다.

시저 암호문을 복호화하기 위해 Python 코드를 사용하였고 코드는 다음과 같다.

```python
def decrypt(c, interval):  # c : 암호문, interval : 밀어낼 문자 간격
    result = ""

    for i in c:
        if ord('A') <= ord(i) <= ord('Z'):
            if ord(i) - interval < ord('A'):
                add_ascii = chr(ord(i) + 26 - interval)
            else:
                add_ascii = chr(ord(i) - interval)

            result += add_ascii

        elif ord('a') <= ord(i) <= ord('z'):
            if ord(i) - interval < ord('a'):
                add_ascii = chr(ord(i) + 26 - interval)
            else:
                add_ascii = chr(ord(i) - interval)

            result += add_ascii
        else:
            result += i

    return result


string = input("Input Cryptogram > ")
interval = int(input("Input Interval > "))

print(decrypt(string, interval))
```

`encrypted.txt` 파일에 DISC로 된 Flag가 존재할 것이라고 예상했기에 {를 검색했더니 역시나 다음과 같이 암호화된 Flag가 존재했다.

![Image](Image_Link.PNG)

DISC에서 QVFP로 암호화된 것을 보니 옮겨진 간격은 13 이라는 것을 알게 되었고, 위의 파이썬 코드에 다음과 같이 값을 넣어주고 결과값을 출력했다.

![Image](Image_Link.PNG)

Flag : **DISC{ceasar_salad_with_no_ceasar}**