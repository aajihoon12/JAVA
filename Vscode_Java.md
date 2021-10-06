# Vscode에서 JAVA 컴파일 및 실행 환경 설정하기


###  vscode는 가볍고 인코딩 환경의 지원이 대단한 개발 도구. 따라서 추가 패키지의 설치와 실행 환경을 조성해야함




## <strong> - JDK 설치 </strong>

#### 1. <https://jdk.java.net> 접속 한다.    

<img src="../images_java/jdk_1.png" width="80%"></img>    

#### 2. 오라클 계정 로그인 후, 자동 설치가 진행 된다.

#### 3. 다운로드 완료 후 압축을 풀어준다. C:\\jdk-14.0.2 가 설치된 것을 확인 할 수 있다.






## <strong> - JAVA 환경 변수 설정 </strong>


#### 4. 다음과 같은 내 컴퓨터->속성->환경 변수의 시스템 환경변수 설정을 완료한다. (총 3가지 변수)

1)변수 이름: JAVA_HOME
2)변수 값: C:\Program Files\Java\jdk-14.0.2

<img src="../images_java/jdk_2.png" width="80%"></img>


1)변수 이름: JDK_HOME
2)변수 값 : C:\Program Files\Java\jdk-14.0.2

<img src="../images_java/jdk_3.png" width="80%"></img>


1)변수 이름: CLASSPATH
2)변수 값: C:\Program Files\Java\jdk-14.0.2\;.;
<strong>(C:\Program Files\Java\jdk-14.0.2까지만 하면 자동으로 뒤에 \;.; 이게 CLASS PATH는 추가)</strong>

<img src="../images_java/jdk_4.png" align="left" width="80%"></img>

1)변수 이름: Path
2)변수 값(추가) : "%JAVA_HOME%\bin"
<strong>(%JAVA_HOME%은 환경 변수 참조를 의미)</strong>


#### 5. 적절한 설치 확인을 위해, CMD 창에서 java -version 명령어를 입력 
<img src="../images_java/jdk_5.png" align="left" width="80%"></img>






## <strong> - VSCODE에 JAVA 환경 SETTING - 확장 프로그램 설치 </strong>


#### 6. vscode에서 자바 실행 환경을 만들기 위해, 확장 패키지 툴을 설치해야한다.(ctrl + shift + x)

(Java Extension Pack)-필수
<img src="../images_java/jdk_6.png" width="80%"></img>

#### 7. File ->Preferences ->Setting 으로 세팅창을 연다 

#### 8. 왼쪽 Extensions -> Java 를 눌러서 스크롤을 쭉 내리면 Home 내용이 나온다

#### 9. Edit in Setting.json 클릭

<img src="../images_java/jdk_7.png" align="left" width="80%"></img>


#### 10. "java.home":"C:\\Program Files\\Java\\jdk-14.0.2 로 변경. Json의 rule에 따라 / -> \\ 로 적어야함

<img src="../images_java/jdk_8.png" align="left" width="80%"></img>

#### 11. cmd창으로 테스트 디렉터리 생성 후 code명령어를 통해, 해당 디렉터리를 vscode로 작업 디렉터리로 실행

<img src="../images_java/jdk_9.png" align="left" width="80%"></img>

#### 12. "New File" 아이콘을 클릭하여, HElloWorld.java로 이름을 설정하고 엔터를 누른다.

<img src="../images_java/jdk_10.png" align="left" width="80%"></img>

#### 13. 다음과 같은 기본 코드를 입력하고, F5("Start Debugging")으로 디버깅한다.

<img src="../images_java/jdk_11.png" align="left" width="60%"></img>

#### 14. 오른쪽 하단에 빌드가 실패했다는 경고가 뜬다.
1)Build failed, do you want to continue? "Procced" -> 변화x
2)Syntax error on token "void", volatile expected 에서 컴파일러가 자바 언어를 이해하지 못한다는 느낌이 컷다.

#### 15. 왼쪽에 있는 launch.json 파일 오픈
1)"mainClass":"${file}" 밑에 "jdkpath":"C:/Program Files/Java/jdk-14.0.2/bin" 을 입력 후 저장

#### 16. 터미널 창을 보면 안정적으로 결과가 나온 것을 볼 수 있다.

<img src="../images_java/jdk_12.png" align="left" width="60%"></img>

