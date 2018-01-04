# MagicTime

## Problem

매직 해쉬란 php가 ==연산을 할 때, 서로 다른 값이 같은 값으로 인식되도록 하는 특수한 동작을 말한다. 
이 특수한 동작이 일어나기 위해서는 조건이 있는데, 바로 문자열을 0e로 시작해야한다는 것이다. 
이를 방지하기 위해 md5와 sha1 등으로 암호화를 했는데, 
암호화를 통한 결과가 0e로 시작되는 경우가 있다고 한다. 그 경우를 찾아 보자!!!

***

## Solution

주어진 링크를 타고 **MagicTime** 문제의 `index.php`로 이동하면 다음과 같은 화면이 나오게 된다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Web/Magic%20Time/Image/index.PNG)

**페이지 소스보기**를 해보면 소스 중간에 주석처리가 되어있는 줄이 하나 있다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Web/Magic%20Time/Image/index_viewsource.PNG)

```html
<!-- ./index.php?view-source -->
```

위의 경로를 URL에 추가하여 들어가면 다음과 같이 문제의 PHP 소스를 볼 수 있다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Web/Magic%20Time/Image/php_source.PNG)

코드를 살펴보면 `$_GET` 방식으로 입력받는 `key2`의 값을 **md5**로 암호화했을 때 나오는 값이 `key1`의 값과 같으면 문제 풀이에 성공하게 된다.

`key1`의 값은 `aabg7XSs`를 `md5`로 암호화시킨 값으로, `0e087386482136013740957780965295` 가 나오게 된다.

이는 `0e`로 시작하게 되어 0 * 10^87386482136013740957780965295 를 한 값이 반환되는데, `0e`로 시작하는 값은 항상 0을 반환하기 때문에 `key2`에는 `aabg7XSs`를 제외하면서 **MagicHash**를 발생시키는 값을 대입하면 된다.

이는 `QNKCDZO`, `240610708` 등이 있기 때문에 이 중 하나를 `key2`에 대입하면 다음과 같이 `Flag`가 주어진다.

![Image](https://github.com/JaehunYoon/CTF/blob/master/2017%20DSM%20CTF/Web/Magic%20Time/Image/flag.PNG)

FLAG : **DISC{THIF_IF_NET_FLAG}**