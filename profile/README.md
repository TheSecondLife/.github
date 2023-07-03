# The Second Life : 시니어의 일상이 새롭게 시작되는 곳

<br/>

![secondLife_main](https://github.com/SahhaShin/coding_test/assets/33896511/23d19c21-807a-4828-bfc6-b14b290863e1)

<br/>

> 개발기간: 2023.06.12 ~ 2023.07.02
> <br/>
> 형태 : App


<br/><br/>


# 배포 주소
> https://yoursecondlife.netlify.app


<br/><br/>


# 개발팀 소개

|지민성|박세윤|석다영|신산하|
|:---:|:---:|:---:|:---:|
|![ms](https://github.com/TheSecondLife/.github/assets/33896511/38fa6812-535c-496d-a9fc-15a60f2305b4)|![sy](https://github.com/TheSecondLife/.github/assets/33896511/4d40dc02-0f62-48c3-98cb-dcabeb572e89)|![dy](https://github.com/TheSecondLife/.github/assets/33896511/ece3b5c5-086a-401c-8597-704c20b1cd2c)|![sh](https://github.com/TheSecondLife/.github/assets/33896511/53234771-3ed7-46fb-8d11-25c54aa05adc)|
|Back & Front|Back|Front|Front|
|<a href="https://github.com/minsung37">@minsung37</a>|<a href="https://github.com/ParkSeYun98">@ParkSeYun98</a>|<a href="https://github.com/Daen12">@Daen12</a>|<a href="https://github.com/SahhaShin">@SahhaShin</a>|


<br/><br/>


# Stacks

### Environment
<img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white"> &nbsp; <img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white"> &nbsp; <img src="https://img.shields.io/badge/Visual Studio Code-007ACC?style=flat-square&logo=Visual Studio Code&logoColor=white"/>


### Config
<img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white">


### Development
<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black"> &nbsp; <img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"> &nbsp; <img src="https://img.shields.io/badge/bootstrap-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white"> &nbsp; <img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"> &nbsp; <img src="https://img.shields.io/badge/mongoDB-47A248?style=for-the-badge&logo=MongoDB&logoColor=white"> &nbsp; <img src="https://img.shields.io/badge/gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white"> &nbsp; <img src="https://img.shields.io/badge/socket.io-010101?style=for-the-badge&logo=socket.io&logoColor=white">


### Communication
> notion 만드는중 ^^


<br/><br/>


# 시작 가이드

### Requirements
For building and running the application you need:

* Front
> react 18.2.0 <br/>
> react-speech-recognition 3.10.0 <br/>
> Node.js 18.16.0 <br/>
> Npm 9.5.1 <br/>
> reduxjs/toolkit 1.9.5 <br/>
> stomp/stompjs 7.0.0 <br/>
> axios 1.4.0 <br/>
> bootstrap 5.3.0 <br/>
> react-bootstrap 2.7.4 <br/>
> http-proxy-middleware 2.0.6 <br/>


* Back
> Spring Boot 3.1.0 <br/>
> java 17 <br/>
> 추가 예정 <br/>

<br/>

### Installation

* Front

```sh
npm install --force
npm start
```

* Back

> 1) build.gradle 클릭 후 실행에 필요한 라이브러리 설치
> 2) src > main > java > util > SecondlifeApplication 좌측 실행 버튼 혹은 우측 상단 실행 버튼 클릭


<br/><br/>


# 프로젝트 구조도
> 준비중입니다.


<br/><br/>


# ERD
![erd](https://github.com/TheSecondLife/.github/assets/33896511/7c4e650c-893b-45b8-873b-b5ed324ae681)


<br/><br/>


# 화면 구성 & 주요 기능
> 준비중입니다.


<br/><br/>


# 업데이트 내역

* 0.1.0
    * 첫 출시 (2023.07.02)
    * 수정: react-speech-kit에서 react-speech-recognition으로 변경
* 0.0.1
    * 작업 진행 중 (2023.06.12)

 
<br/><br/>


# Trouble Shooting

### CORS: Cross Origin Resource Share
> 문제 사항: 프론트엔드에서 백엔드로 API 요청 시 CORS 에러<br/>
> 해결 방안: Http-Proxy-Middleware 패키지 설치 및 setupProxy.js 배치<br/>
```sh
const { createProxyMiddleware } = require("http-proxy-middleware");

// src/setupProxy.js
module.exports = function (app) {
    app.use(
        createProxyMiddleware("/api", {
            target: process.env.REACT_APP_SERVER,
            changeOrigin: true,
        })
    );
};
```
> 개념: 프록시 서버는 클라이언트가 프록시 서버를 통해 다른 네트워크에 간접적으로 접속할 수 있게 해준다. 쉽게 이해하자면 "중계서버"라고 이해하면 된다.<br/>
> 출처: https://velog.io/@yunsungyang-omc/React-React-App%EC%97%90%EC%84%9C-CORS-%EC%9D%B4%EC%8A%88-%ED%95%B4%EA%B2%B0%ED%95%98%EA%B8%B0

<br/>

### Redux Toolkit 재렌더링 이슈
> 문제 사항: Redux Toolkit 재렌더링 시 내부 데이터가 초기화되는 이슈<br/>
> 해결 방안1: redux-persist 적용해 local storage에 정보 저장하려 했지만 제대로 동작 안함<br/>
> 해결 방안2: local storage로 다음 페이지에 필요한 정보만 저장하는 방향으로 진행 (채택)<br/>

<br/>

### react-speech-kit 앱 버전 이슈
> 문제 사항: 버튼을 길게 눌러 음성을 인식하는 구조, 핸드폰 웹에서는 작동 안됨<br/>
> 해결 방안: react-speech-recognition을 이용해 [start] 버튼 클릭 후 음성 인식, [stop] 버튼 클릭 후 인식 중단<br/>
> 추가 문제점: 리액트 웹을 앱으로 다운받았을 때 버튼이 안눌리는 이슈 발생<br/>
