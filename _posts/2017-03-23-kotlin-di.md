---
layout: post
categories: Study
tags: [Kotlin, DI]
author: Gudnam
title: Kotlin에 DI 패턴을 적용해보자!
---
<div class="message"> 
좋은 프로그램은 객체간 혹은 모듈간의 결합성이 낮을수록 좋다고 한다
</div> 

# 개념 간단히 살펴보기

## DI ?

> Dependency Inject

[쉽게 설명해 놓은 슬라이드 쉐어](https://www.slideshare.net/baejjae93/dependency-injection-36867592)

	좋은 프로그램은 객체간의 결합성(Coupling), 의존성(Dependency)가 낮을수록 좋다고 한다
	Coupling, Dependency를 낮추기 위해 탄생한 개념이 DI 패턴이다

* A, B 두 객체가 있다
* A가 B를 연결하기 위해서는 객체를 생성, 초기화 하는 작업이 필요하다
{% highlight js %}
// ex) Java
B b = new B("init");
{% endhighlight %}
![di1](/public/img/di1.png)
* 하지만 A 객체에서 B를 생성했다는 것은 A는 B에 종속되고 있다는 뜻이다
* 종속 됐다는 말은 만약 B가 변경되면 A도 어쩔 수 없이 변경된다는 것이다
![di2](/public/img/di2.png)
* 방법은 A가 B를 생성하지 말고, 외부의 무언가가  B를 생성하고 그걸 A한테 주면(Inject) 된다
![di3](/public/img/di3.png)
* A와 B는 이제 한결 멀어졌다


# MVP 적용한 코드 위에 DI 패턴을 적용해보자!

## 개발을 위한 환경설정
> Dagger2 framework

### Dagger2
> DI Framework

{% highlight js %}
// app/build.gradle
...

dependencies {
  kapt "com.google.dagger:dagger-compiler:$daggerVersion"
  compile "com.google.dagger:dagger:$daggerVersion"
  ...
}
{% endhighlight %}

## DI 적용 

작성중...
