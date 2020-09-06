2020.09.07(월) 03:46
---

## 문제

docker 공부할겸, docker-compose 테스트를 위해 젠킨스를 설치하는데 젠킨스 플러그인 설치시 다음과 같은 오류가 나왔다.

![스크린샷 2020-09-07 오전 3 47 29](https://user-images.githubusercontent.com/50758600/92333013-f3060f80-f0bc-11ea-9f58-ac8af3bd8f72.png)

## 원인

해당 이유에 대한 검색 결과 젠킨스의 버전이 낮아 그렇다는 것을 알게 되었다. 내가 실습에 사용한 젠킨스 버전은 2.142-slim이다. 

~~~
master    | Caused by: java.io.IOException: Email Extension Plugin v2.75 failed to load.
master    |  - JUnit Plugin v1.29 failed to load. Fix this plugin first.
master    |  - You must update Jenkins from v2.142 to v2.164.3 or later to run this plugin.
~~~

## 해결 방법

1. 현재 jenkinsci/jenkins:2.255-slim 이미지를 사용하고 있어서, jenkins/jenkins:2.235.5-lts 버전을 적용하여 실행을 해보도록했다. 

- 참고로 최신 버전은 [도커 허브](https://hub.docker.com/r/jenkins/jenkins/tags)를 확인하면 된다.

다행히 정상적으로 설치되었다!

![스크린샷 2020-09-07 오전 4 19 07](https://user-images.githubusercontent.com/50758600/92333551-55610f00-f0c1-11ea-916f-bf8da616b345.png)
