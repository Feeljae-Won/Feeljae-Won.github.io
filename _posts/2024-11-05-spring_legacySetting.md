---
title: "[Spring Framework] 스프링 레거시 프로젝트 세팅 - STS3 설치"
date: 2024-11-05 19:00:00 +0900
categories:
  - docs
  - spring
  - spring framework
tags:
  - spring
  - spring framework
  - spring setting
layout: single
---
# [Spring Legacy Project 세팅] - STS3 설치

## STS (Spring Tool Suite)
- STS란 Spring Framework를 지원하는 IDE (Intergrated Development Environment, 통합 개발 환경) 개발 Tool 중 하나로 Java 기반의 웹 서비스 어플리케이션 구축을 할 수 있도록 도와주는 개발 도구 이다. (Spring Framework Plugin이 미리 설치 되어 있는 이클립스라고 생각하면 된다.)
- 기본 이클립스에서도 마켓 플레이스를 통해 Spring Framework Plugin을 추가로 설치할 수 있지만, 이클립스 버전에 따라 오류가 발생할 수 있다.

### STS3, STS4의 차이
- **STS3** 스프링 MVC프로젝트(Spring MVC Project)나 메이븐(Maven) 등 기본 설정이 미리 준비된 스프링 프로젝트를 사용하려면 STS3를 설치해야 한다.
- **STS4** 스프링 부트 (Spring Boot)를 사용하는 환경을 사용하려면 STS4를 설치해야 한다.

### 다운로드
- STS3는 [https://github.com/spring-attic/toolsuite-distribution/wiki/Spring-Tool-Suite-3](https://github.com/spring-attic/toolsuite-distribution/wiki/Spring-Tool-Suite-3) 에서 받을 수 있다.
- 또는 다음 링크에서 다운로드 가능하다. [https://download.springsource.com/release/STS/3.9.18.RELEASE/dist/e4.21/spring-tool-suite-3.9.18.RELEASE-e4.21.0-win32-x86_64.zip](https://download.springsource.com/release/STS/3.9.18.RELEASE/dist/e4.21/spring-tool-suite-3.9.18.RELEASE-e4.21.0-win32-x86_64.zip) <- 다운로드

### STS3 설정
- STS 환경 설정은 크게 3가지 설정이 필요하다.
   - STS가 사용할 JVM 지정
   - 인코딩 변경
   - WAS 연동 (Apach Tomcat)

#### STS JVM 지정
1. `STS.exe` 실행 -> `Window` -> `Preferences` 메뉴 클릭
2. `JAVA` -> `installed JREs` 클릭
3. 포함된 `jre` 선택후 `Remove` 클릭
4. `Add...` 클릭
5. `Standard VM` 클릭 후 `Next` 버튼 클릭
6. `Directory...` 버튼 클릭, 추가 하려는 JDK가 설치된 폴더 지정 (예: `C:\java\jdk-11`)
7. `Finish` 버튼 클릭
8. 설정한 JDK 폴더 체크 확인 후 `Apply and Close` 버튼 클릭

#### Encoding 변경
1. 워크스페이스 인코딩 설정 경로
   - `window` - `Prefernces` - `General` - `Workspace` - `Textfile encoding` - `UTF-8`

2.  `HTML`, `CSS`, `JSP` 인코딩 설정 경로
   - `Window` - `Prefernces` - `Web` - `HTML Files`/`CSS Files`/`JSP Files` - `Creating files` - `Encoding` - `UTF-8`

#### WAS 설정
- Apache Tomcat 다운로드 후 서버 설정
