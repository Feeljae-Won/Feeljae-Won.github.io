---
title: "[Java] 클래스 - )오버로딩(Overloading)과 오버라이딩(Overriding)의 차이"
categories:
  - docs
  - java
tags:
  - java
layout: single
---

# 오버로딩(Overloading)과 오버라이딩(Overriding)
- 오버라이딩(Overriding)과 오버로딩(Overloading)은 자바에서 메서드를 다루는 중요한 개념이다. <br>
	둘 다 비슷해 보이지만 완전히 다른 역할을 한다.

## 오버라이딩(Overriding)
- 오버라이딩은 부모 클래스에 있는 메서드를 자식 클래스에서 재정의하는 것을 말한다. <br>
	부모 클래스에 이미 정의된 메서드를 자식 클래스에서 다시 작성해 "이렇게 동작하도록 하겠다"라고 변경하는 것이다.
```java
class Animal {
    public void speak() {
        System.out.println("동물이 소리를 낸다.");
    }
}
```
```java
class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("강아지가 멍멍!");
    }
}
```
```java
public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        myDog.speak();  // "강아지가 멍멍!" 출력
    }
}
```
- 이 코드에서 `Dog` 클래스는 `Animal` 클래스의 `speak()` 메서드를 오버라이딩했다. 부모의 메서드 대신, `Dog` 클래스가 재정의한 메서드가 호출된다.

## 오버로딩(Overloading)
- 오버로딩은 같은 이름의 메서드를 여러 번 정의하는 것을 말한다. 하지만 매개변수의 개수나 타입이 달라야 한다. 예를 들어, 숫자를 더하는 메서드를 다양한 방식으로 정의할 수 있다.
```java
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }
}
```
```java
public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(3, 4));        // 7
        System.out.println(calc.add(2.5, 4.5));    // 7.0
        System.out.println(calc.add(1, 2, 3));     // 6
    }
}
```
- 이 코드에서 `add()` 메서드는 세 가지 방식으로 오버로딩되어 있다. 각각의 메서드는 매개변수에 따라 다르게 호출된다.

## 차이점 요약
* 오버라이딩은 부모 클래스의 메서드를 자식 클래스에서 재정의하는 것.
* 오버로딩은 같은 이름의 메서드를 다른 매개변수로 여러 번 정의하는 것.<br><br>
오버라이딩은 상속받은 메서드를 자식이 `"내 방식대로 하겠다"`라고 덮어쓰는 것이고, 오버로딩은 `"같은 이름으로 여러 가지 일을 할 수 있다"`라고 생각하면 된다.

