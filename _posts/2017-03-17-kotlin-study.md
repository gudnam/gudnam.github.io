---
layout: post
categories: Study
tags: [Kotlin, Bandhook]
author: Gudnam
title: BandHook App 분석
---
<div class="message"> 
	최근에 아이오에서 베타로 나갈 데모 서버 개발을 진행하게 됐는데 이 때 스칼라라는 함수형 언어를 처음 써봤다. 참 매력적이더라. 다음 안드로이드 앱은 코틀린으로 간다! Github 에서 Bandhook 이란 좋은 샘플을 발견해 공부해보기로 했다~!
</div> 

나는 MVP 패턴을 즐겨 쓴다. 테스트 코드 작성하기 편하기 때문이다. Bandhook 도 MVP 모델을 사용하는데 DI를 통해 구현한게 참 인상깊었다.

+ MVP 모델 + DI
	- abstract BaseActivity
		- 모든 Activity 가 BaseActivity 를 상속
		- abstract 로 layout, di
	- DI
		- DI 적용하기 위해서는
		- Component 에 Module 을 추가해야 함
		- Main에서 DI 를 사용하려면 MainModule 을 생성해서 추가 해야 함
		- Module 에서는 DI 를 사용하고자 하는 class 를 @Provide 를 통해 등록할 수 있음
		- 등록이 모두 완료되면 @Inject 를 사용해 DI 사용
+ Test Code

---
 
+ 모르는 개념
	+ Module
	+ DaggerApplicationComponent

+ 모르는 Annotation
	+ @Component
	+ @Provide	
+ 모르는 문법
	- Inject Annotation (@Inject)
		- Spring 에서의 @Autowired
		- 의존관계를 자동적으로 설정할 때 사용
	- lateinit & by lazy
		- by lazy deligate 랑 유사하지만 약간 다름
		- by lay 는 val 에서 사용 가능
		- lateinit 은 var 에서 사용 가능
		- by lazy
			- ``the first call to get() executes the lambda passed to lazy() and remembers the result, subsequent calls to get() simply return the remembered result.``
			- by lazy 로 선언된 상수는 호출될 때 처음 호출할 때 그에 대한 결과 값을 기억하고 그 후에는 호출될 때는 저장했던 값을 보여준다.
			- 만약 by lazy 를 사용하지 않는다면 (엄격성 사용시) 호출할 때 마다 결과 값을 불러오는 작업이 내부적으로 있을 것이다.
			- 캐시해놓고 있다가 다음에 불려질 땐 캐시된 값을 불러온다고 생각하면 될 듯
		- lateinit
			- 
	- find & findOptional 이란?
		- layout 과 kotlin 매칭 시키는 기능인듯
		- findOptional 은 null 허용인듯
		- kotlin extension 을 사용해 생략할 수 있음
	- Backing Fields
		- 코틀린에서의 class 는 필드가 없다.
		- 그러나 때로는 
	- extends 와 implemets 를 구분하는 방법은 ()가 있냐 없냐?
		- 클래스를 상속 받을 때는 : parent() 로 쓰고
		- 인터페이스를 구현할 때는 : parent 로 씀
		- 인터페이스에는 생성자가 없어서 그런가 보다
	- navigate
	- when
	- companion object
		- [관련 링크](http://kunny.github.io/lecture/kotlin/2016/07/10/kotlin_companion_object/)
		- Java 에서 public static final ?? 용법을 사용하기 위한 것
		- Foo.bar 같이 사용하기 위한 정적 선언
		- Java 에서도 코틀린 정적 변수를 깔끔하게 가져오기 위함
- 모르는 라이브러리
	- greenrobot eventbus
		- Activity <-> Activity, Activity <-> Fragment, Fragment <-> Fragment
		- 위와 같은 화면간의 통신이 안드로이드에서는 귀찮은 작업이다
		- 이것을 이벤트버스를 통해 쉽게 데이터를 전달 받고 전달할 수 있게 한다
	- picasso
		- 이미지 처리 라이브러리
		- 이미지 캐싱, 로드 실패시 처리, 가져온 이미지 프로세싱 등 작업
	- android-priority-jobqueue
		- [참고 사이트](https://github.com/path/android-priority-jobqueue)
		- 백그라운드 서비스를 효율적으로 해줌
	- jetbrains anko
		- [참고 사이트](https://github.com/Kotlin/anko)
		- UI를 프로그래밍하는데 있어 보다 쉽고 깔끔하게 개발이 가능하게 해줌
	- dagger
		- DI 를 위한 라이브러리
		- [참고 사이트](http://drcarter.tistory.com/169)
		- 중요한 annotation
			-  @Module : 객체를 Module로 구성, 내부에서 주입될 객체들을 provide해주는 것.
			-  @Provides : 객체 주입에 필요한 내용을 리턴해주는것
			-  @Component : Module과 Inject간의 Bridge같은 역활.
			-  @Inject : 객체의 의존성 주입
- 모르는 Annotation
	- Qualifier
		- 안드로이드에는 자료가 거의 없어 [Spring 에서 어떻게 사용하는지](http://crystalpark.tistory.com/17) 확인
		- 의존관계를 맺는데 예상치 못한 예외에 대비해 좀더 확실히 의존관계를 맺기 위해 설정하는듯

다음에는 직접 코틀린 기반의 Framework 를 만들어보려고 한다. 이곳에 나오는 개념을 많이 참고할듯!
