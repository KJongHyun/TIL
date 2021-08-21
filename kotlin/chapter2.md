# 함수와 변수
## fun

코틀린 함수 표기법
```kotlin
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
```
코틀린에서 if는 식 -> 값을 반환

식이 본문인 함수  
```kotlin
fun max(a: Int, b: Int): Int = if (a > b) a else b
```

코틀린은 정적 타입 지정 언어이므로 컴파일 시점에 모든 시그이 타입을 지정, 본문 식 분석을 통해 반환 타입 추론 가능  

## 변수
### val(value)
변경 불가능한(immutable) - 자바의 final
### var(variable)
변경 가능한(mutable) - 자바의 일반 변수

## 문자열 템플릿 
```kotlin
val name = "jonghyeon"
println("My name is $name")
```

## 클래스와 프로퍼티

```kotlin
class Person(val name: String)
```
변수 선언과 생성자 초기화를 동시에 간편한게

### 프로퍼티
코틀린의 프로퍼티는 자바의 필드와 접근자 메소드를 완전히 대체
val -> read-only (getter만 생성)
var -> read & write (getter, setter 생성)

### 커스텀 접근자
```kotlin
class Rectangle(val height: Int, val width: Int) {
    val isSquare: Boolean
    get() {
        return height == width
    }
}
```

## 선택 표현과 처리: enum과 when  
### enum  
```kotlin
enum class Color(val r: Int, val g: Int, val b: Int) {
    RED(255, 0, 0), ORANGE(255, 165, 0) // ...
    
    fun rgb() {
        println("$r, $g, $b")
    }
}
```

### when  
```kotlin
when (color) {
    Color.RED -> "빨강"
    Color.ORANGE -> "주황"
}
```

```kotlin
when (color) {
    Color.RED, Color.ORANGE, Color.GREEN -> "신호등 색"
}
```

```kotlin
fun mix(color1: Color, color2: Color) {
    when (setOf(color1, color2)) {
        setOf(Color.RED, Color.YELLOW) -> ORANGE
        else -> // ~~~
    }
}
```

## while과 for 루프
### while
java와 동일

### for
구간 설정 ex) 1..10
```kotlin
for (i in 1..10) {
    println(i)
}
```
```kotlin
for (i in 100 downTo 1 step 2)
```
```kotlin
for (i in 1 until 100)
```
```kotlin
for (c in 'A'..'F') {
    val binary = Integer.toBinaryString(c.toInt())
}
```

```kotlin
for ((letter, binary) in binaryReps) {
    println("$letter = $binary")
}
```



