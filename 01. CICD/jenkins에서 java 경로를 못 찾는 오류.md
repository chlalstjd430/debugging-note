2020.09.07(월) 20:17

## 문제

젠킨스 slave 컨테이너 구축시 다음과 같은 문구가 나옴.

~~~
[09/07/20 11:03:30] [SSH] Checking java version of /home/jenkins/jdk/bin/java
Couldn't figure out the Java version of /home/jenkins/jdk/bin/java
bash: /home/jenkins/jdk/bin/java: No such file or directory

[09/07/20 11:03:30] [SSH] Checking java version of java
Couldn't figure out the Java version of java
bash: java: command not found

[09/07/20 11:03:30] [SSH] Checking java version of /usr/bin/java
Couldn't figure out the Java version of /usr/bin/java
bash: /usr/bin/java: No such file or directory

[09/07/20 11:03:30] [SSH] Checking java version of /usr/java/default/bin/java
Couldn't figure out the Java version of /usr/java/default/bin/java
bash: /usr/java/default/bin/java: No such file or directory

[09/07/20 11:03:30] [SSH] Checking java version of /usr/java/latest/bin/java
Couldn't figure out the Java version of /usr/java/latest/bin/java
bash: /usr/java/latest/bin/java: No such file or directory

[09/07/20 11:03:30] [SSH] Checking java version of /usr/local/bin/java
Couldn't figure out the Java version of /usr/local/bin/java
bash: /usr/local/bin/java: No such file or directory

[09/07/20 11:03:30] [SSH] Checking java version of /usr/local/java/bin/java
Couldn't figure out the Java version of /usr/local/java/bin/java
bash: /usr/local/java/bin/java: No such file or directory

java.io.IOException: Java not found on hudson.slaves.SlaveComputer@27eabc60. Install a Java 8 version on the Agent.
	at hudson.plugins.sshslaves.JavaVersionChecker.resolveJava(JavaVersionChecker.java:82)
	at hudson.plugins.sshslaves.SSHLauncher$1.call(SSHLauncher.java:442)
	at hudson.plugins.sshslaves.SSHLauncher$1.call(SSHLauncher.java:412)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	at java.lang.Thread.run(Thread.java:748)
[09/07/20 11:03:30] Launch failed - cleaning up connection
[09/07/20 11:03:30] [SSH] Connection closed.
)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	at java.lang.Thread.run(Thread.java:748)
[09/07/20 11:14:42] Launch failed - cleaning up connection
[09/07/20 11:14:42] [SSH] Connection closed.
~~~

## 문제 원인ㄷ

자바 경로를 찾을 수 없어서 그렇다.

## 문제 해결

host container에서 "java which" 명령어를 이용해 java 경로를 파악후 해당 경로를 다음과 같이 환경변수에 추가하여 해결 함.

![스크린샷 2020-09-07 오후 8 20 26](https://user-images.githubusercontent.com/50758600/92382457-94d23e80-f147-11ea-9fbc-ac2256910a2c.png)
