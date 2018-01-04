# Mixed Breed

## Problem

String Replace는 쉽게 말해 문자열의 형태를 바꿔주는 것이다. 
str_replace("king","queen","theking"); 을 예시로 들면 theking이라는 문자열에서 
king을 queen으로 바꿔주라는 말이다. 

Decoding 즉 복호화는 암호화된 정보를 암호화되기 전으로 돌리는 처리 혹은 그 방법을 말한다. 
base64 암호화 방식은 그 끝이 =으로 끝나서 알아보기 쉽다. 

해시암호란 평문 즉 어떠한 문장을 해시알고리즘을 통해 해시값으로 출력하는 것을 말한다. 
띄어쓰기 등의 약간의 변화에도 해시값은 완전 다른 값이 나오기 때문에, 
해시값은 주로 데이터의 위,변조여부를 확인하는데 사용된다. 

해시함수의 종류는 MD5, SHA-1, SHA 224 등이 있다. 
아 참고로 Mixed breed는 혼종이라는 말이다. 

HINT : 복호화

***

## Solution

주어진 링크를 타고 **Mixed Breed** 문제의 `index.php`로 이동하면 다음과 같은 화면이 나오게 된다.

![Image](Image_Link.PNG)


`Password`와 `Passcode`를 입력받는 폼이 존재하고 **페이지 소스 보기**를 해보면 다음과 같이 눈에 띄는 주석이 있다.

![Image](Image_Link.PNG)

```html
<!-- VEdrNWNHSnRVbXhsUXpWM1lVaEJMMk15T1RGamJVNXNXVEk1YTFwUlBUMD0= -- >
```
주석에는 끝 부분이 =로 되어있는 코드로 되어져 있었는데 **base64**로 암호화된 코드는 끝이 =로 끝나기 때문에 주석에서 주어진 코드가 **base64**로 암호화된 코드임을 알 수 있다.

이를 3번 정도 디코딩시키면 `./index.php?sourcecode` 가 나오게 되며 `index.php`의 URL에 위와 같이 `?sourcecode`를 대입하면 다음과 같은 PHP 소스코드를 볼 수 있게 된다.

![Image](Image_Link.PNG)


```php
$input_password=str_replace("best","",$_GET["password"]);
```
`str_replace` 함수에서 password 값에 `best`가 들어있으면 이를 빈 값으로 치환시킨다.

일치해야하는 `password` 값은 `lapio best` 인데, 이는 `str_replace` 취약점을 이용하여 `lapio bbestest` 와 같이 password 값을 넣어주면 `lapio best`와 같은 `password` 값을 가지게 된다.
***
`$_GET` 방식으로 입력받는 Passcode는 조건문을 보면 4를 초과하면서 5 미만의 값을 가지고 있어야 하는데, 이는 Passcode에 4와 5 사이의 실수를 입력하여 `hint`를 출력시킬 수 있다.

조건을 충족하는 Password와 Passcode를 입력해주면 출력되는 `hint`는 다음과 같다.

![Image](Image_Link.PNG)

`7e432d6f6cc2100e03523d8985c914f3ca3f522af7799564d48c37af231c9d5b9acbc45201e139cdab4a01c7aadb4f8e4f9a2990eb3ef699f6495055cedea0d4` 를 문제에서 Hint로 제공해주었던 복호화 사이트에서 복호화시키면 다음과 같은 `hint`가 나오게 된다.

![Image](Image_Link.PNG)

`hint`에서 주어진 경로를 URL로 진입하면 다음과 같이 `Flag`가 주어진 페이지를 볼 수 있다.

![Image](Image_Link.PNG)

FLAG : **DISC{WH2_5O_S2RIOU5}**