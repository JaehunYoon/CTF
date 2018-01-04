# Web MIC Check

## Problem

마이크 테스트

***

## Solution

주어진 링크를 타고 **Web MIC Check** 문제의 `prob.html`로 이동하면 다음과 같은 화면이 나오게 된다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Web/Web%20MIC%20Check/Image/prob.PNG)

> Hello World!!<br/>
> Hmm.. how about view source..?

대놓고 소스를 보는 것은 어떠냐고 한다.
문제에서 시키는대로 **페이지 소스 보기**를 해보면 다음과 같이 소스코드 사이에 `Flag`가 주석 처리 되어있는 것을 볼 수 있다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Web/Web%20MIC%20Check/Image/flag.PNG)

FLAG : **DISC{MIC_CH3CK_AAAAA}**