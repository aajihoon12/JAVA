# Vscode에서 JAVA 컴파일 및 실행 환경 설정하기



### vscode는 가볍고 인코딩 환경의 지원이 대단한 개발 도구 따라서 추가 패키지의 설치와 실행 환경을 조성해야함






## <strong> - JDK 설치 </strong>

#### 1. <https://jdk.java.net> 접속 한다.    

<img src="../images/jdk_1.png"></img>    

#### 2. 오라클 계정 로그인 후, 자동 설치가 진행 된다.

#### 3. 다운로드 완료 후 압축을 풀어준다. C:\\jdk-14 가 설치된 것을 확인 할 수 있다.







## <strong> - JAVA 환경 변수 설정 </strong>


#### 4. 다음과 같은 내 컴퓨터->속성->환경 변수의 시스템 환경변수 설정을 완료한다. (총 3가지 변수)

변수 이름: JAVA_HOME
변수 값: C:\Program Files\Java\jdk-14.0.2
<img src="../images/jdk_2.png"></img>


변수 이름: JDK_HOME
변수 값 : C:\Program Files\Java\jdk-14.0.2
<img src="../images/jdk_3.png"></img>


변수 이름: CLASSPATH
변수 값: C:\Program Files\Java\jdk-14.0.2\;.;
<strong>(C:\Program Files\Java\jdk-14.0.2까지만 하면 자동으로 뒤에 \;.; 이게 CLASS PATH는 추가)</strong>

<img src="../images/jdk_4.png" align="left"></img>

변수 이름: Path
변수 값(추가) : "%JAVA_HOME%\bin"
<strong>(%JAVA_HOME%은 환경 변수 참조를 의미)</strong>


#### 5. 적절한 설치 확인을 위해, CMD 창에서 java -version 명령어를 입력 
<img src="../images/jdk_5.png"></img>








## <strong> - VSCODE에 JAVA 환경 SETTING - 확장 프로그램 설치 </strong>

