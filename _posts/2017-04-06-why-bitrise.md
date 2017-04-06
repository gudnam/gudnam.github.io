---
layout: post
categories: CI
tags: [Android, Bitrise, CI]
author: Gudnam
title: 왜 안드로이드 CI로 Bitrise를 선택했을까?
---
## 무엇을 기준으로 선정할 것인가?

+ 모바일 환경에 적합한지
+ 테스트 환경 적합한지
  + Unit testing, UI testing, Cloud device testing ...
+ 환경 설정이 얼마나 간편한지

## CI 후보

+ **Bitrise**
+ CircleCI
+ Jenkins

## 왜 Bitrise를 선택했는가?

#### 모바일 환경에 적합하다

+ Jenkins와 그 외 다른 CI 들은 모바일 뿐 아니라 정말 다양한 환경을 지원하는 멀티 플랫폼이다
  + CircleCI도 모바일 지원이 강력하지만 Bitrise 는 오직 모바일
+ 그러다 보니 수동으로 설정해야 할 것들이 꽤 많다
  + 예를 들어 keystore를 저장할 경우 CircleCI 는 DropBox 와 연동해야 하는 번거로움이 있다
+ Bitrise는 Android, iOS에 특화 돼 있어 많은 편한 기능들을 제공한다
  + 빠른 빌드 속도
  + 기본적인 설정 모두 지원
  + 여러 Integration 지원

#### 테스트 환경에 적합하다

+ Unit testing, UI testing, Cloud device testing은 대부분 지원한다
+ UI tesing framework는 Cloud device testing framework를 이용할 것이기 때문에 중요도 낮춤
  + Calabash, Appium 둘 중 하나를 선택할건데 다 지원함
  + Bitrise는 Calabash를 강력하게 지원
+ Cloud device testing
  + AWS Device Farm, Xamarin Cloud Test 둘 중 하나 생각중
  + Bitrise 에서 두개 다 지원
  + 특히 Xamarin을 강력하게 지원

#### 환경 설정이 얼마나 간편한가

+ Bitrise의 UI Workflow 가 굉장히 직관적이다
  + 원하는 Integration을 쉽게 적용할 수 있다
+ CLI도 지원해 익숙해지면 간편하게 터미널로 작업할 수 있다
+ 기본 CI 설정에서 Dependency가 없다
  + Preset 매우 간편하고 빠르게 적용 가능

#### 그 외

  + 오픈소스이기 때문에 유용한 Integration 이 많고 빠르게 추가되기 좋은 구조

