---
layout: post
categories: Study
tags: [Kotlin, Architecture]
author: Gudnam
title: Android + Kotlin + Clean Architecture
---

# Kotlin Framework Architecture for Android

참고
+ https://fernandocejas.com/2014/09/03/architecting-android-the-clean-way/
+ https://news.realm.io/kr/news/clean-architecture-in-android/
+ BandHook App

## IO Kotlin Framework Architecture
![kotlin architecture](/public/img/kotlin-framework-architecture/Kotlin Framework Architecture.png)

![package tree](/public/img/kotlin-framework-architecture/package tree.png)

## 4Layers Architecture

**Presentation, Data, Domain, Entity**

![4layer](https://fernandocejas.com/assets/migrated/clean_architecture1.png)

Dependency는 각 Layer에서 밖에서부터 안으로 갈 수록 깊어진다.
(Presentation은 Data를 알고 Data는 Domain을 알고 Domain은 Entity를 알고 있다)

![schema](https://fernandocejas.com/assets/migrated/clean_architecture_android.png)

### Presentation Layer

안드로이드의 View나 Animation 등을 처리한다. View를 처리하기 위한 MVC, MVP, MVVM 등 여러가지 모델이 있다. 사용자의 액션을 받아 Domain Layer 로 전달한다.

### Domain Layer

사용자의 Use case를 구현한다. 여기서 주의할 점은 Domain에서는 플랫폼(Android, iOS...)에 의존적이지 않다는 것이다. 예를 들어 '버튼을 눌렀을 때 불을 켠다'의 기능을 구현한다고 할 때 Domain에서는 OS로부터 불켜는 이벤트를 받거나, 블루투스로 불을 켜는 메시지를 전달하는 것은 제외한다. 플랫폼과 상관 없이 순수한 개발 언어로 구현한다.

### Data Layer

데이터를 저장하거나 불러오는 기능을 담당한다. 여기서 데이터 위치는 DB, 서버 연동, 메모리 등 모든 저장공간을 포함한다.

### Entity Layer

단일체로서 여러 용례가 있다. 여기서는 관계형 데이터베이스에 저장될 수 있는 어떤 데이터에 관한 사람 ,장소 또는 사물이다. 또한 데이터 모델링 관점에서는 분류될 수 있고 다른 Entity들에 대해 정해진 관계를 가지는 데이터 단위이다. Entity는 ERD(Entity Relationship Diagram)으로 표현 할 수 있어야 한다.

