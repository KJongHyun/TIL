# 클래스, 객체, 인터페이스

## 클래스 계층 정의  
### 코틀린 인터페이스  
```kotlin
interface Clickable {
    fun click()
    fun showOff() = println("I'm clickable!") // 디폴트 구현이 있는 메소드
}
```
- 코틀린 인터페이스는 자바8 인터페이스와 비슷  
- 추상 메소드뿐 아니라 구현이 있는 메소드도 정의할 수 있다(자바 8의 디폴트 메소드와 비슷)  

```kotlin
class Button : Clickable {
    override fun click() = println("I was clicked")
}
```

코틀린에서는 extends와 implements 키워드 구분없이 콜론(:)을 붙여서 모두 처리
자바의 @Override 어노테이션과 비슷한 override 변경자는 프로퍼티나 메소드를 오버라이드한다는 표시. 자바와 달리 필수로 사용됨

```kotlin
class Button : Clickable, Focusable {
    override fun click() = println("I was clicked")
    override fun showOff() {
        super<Clickable>.showOff()
        super<Focusable>.showOff()
    }
}
```

- 두 상위 타입의 구현을 호출할 때는 super를 사용  
- 구체적 타입을 지정하는 문법 super<Clickable>.showOff() 과 같은 형태로 사용  

### open, final, abstract 변경자: 기본적으로 final  
- 자바에서는 기본적으로 모든 클래스는 상속이 가능 (open)
- 코틀린에서는 클래스와 메소드가 기본적으로 상속 불가능 (final)
- 코틀린에서도 클래스를 abstract로 선언할 수 있다.   
  - abstract로 선언한 추상 클래스는 인스턴스화할 수 없다.
  - 추상 클래스에는 구현이 없는 추상 멤버가 있기 때문에 하위 클래스에서 그 추상 멤버를 오버라이드해야한다.  
  - 추상 멤법는 항 상 열려있기 때문에 "open" 변경자 명시할 필요 없음

### 가시성 변경자: 기본적으로 공개
코틀린의 기본 가시성은 public (자바의 경우 package-private)  

| 변경자 | 클래스 멤버 | 최상위 선언 |  
| :------ | :------ | :------ |  
| public | 모든 곳에서 볼 수 있다. | 모든 곳에서 볼 수 있다. |  
| internal | 같은 모듈 안에서만 볼 수 있다. | 같은 모듈 안에서만 볼 수 있다. |
| protected | 하위 클래스 안에서만 볼 수 있다. | (최산위 선언에 적용할 수 없음) |
| private | 같은 클래스 안에서만 볼 수 있다. | 같은 파일 안에서만 볼 수 있다. |

### 내부 클래스와 중첩된 클래스: 기본적으로 중첩 클래스
코틀린은 상위 class 내부에 class를 선언하면 기본적으로 중첩클래스(자바의 static class)  
내부 클래스로 선언해서 사용하기 위해서는 inner 키워드 사용 필요  

## 뻔하지 않은 생성자와 프로퍼티를 갖는 클래스 선어
### 클래스 초기화

## 컴파일러가 생성한 메소드: 데이터 클래스와 클래스 위임  
### 모든 클래스가 정의해야 하는 메소드  
- 코틀린 동등성 연산에 == 사용 -> 자바의 equals  
- 코틀린의 참조 비교 === 사용 -> 자바의 참조타입 ==  
