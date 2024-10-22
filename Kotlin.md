# Kotlin
## Concepts
### 비교
- Boolean의 경우 `if (a?.b?.isTraded ?: false)` 보다는 `if (a?.b?.isTraded == true)` 와 같은 방식으로 구현한다.

### Custom accessor VS Function
- 행동을 나타내는 개념이면 Function
- 상태나 값등 정보를 가져오는 개념이면 Custom accessor

> [Kotlin: should I define Function or Property?](https://blog.kotlin-academy.com/kotlin-should-i-define-function-or-property-6786951da909)

### Labmda
- invoke() 함수는 nullable이 아닐 때에는 생략해서 사용한다.
```kotiln
val foo: () -> Unit
val bar: (() -> Unit)?

foo.invoke() // X
foo() // O
bar?.invoke() // O
```

## Naming Rules
### Package
- package 이름은 소문자로 작성한다.
```kotlin
package kr.co.prnd.domain
```
- underscore(`_`)는 사용하지 않는다.
```kotlin
// WRONG!
package kr.co.prnd.domain_module
```
- Android의 [kotlin-style-guide](https://developer.android.com/kotlin/style-guide#package_names)의 **항상 소문자로만 작성**하라는 지침을 따른다.

### 함수 이름
- ViewModel을 observe()할때 모아놓는 함수 이름
```kotlin
setupObserver()
```

- 서버에서 데이터를 불러올때 함수 이름
```kotlin
fetchXXX()
```

- 서버에 저장할때 함수 이름
```kotlin
saveXXX()
```

- Return이 있는 데이터를 불러올때 함수 이름
```kotlin
getXXX()
```

- 특정 객체를 찾는 함수 이름
```
findXXX()
```

- 복수형을 가져올때의 함수 이름
    - 변수형에 의존하지 않는 네이밍을 지향한다.
```kotlin
getBrands()      // O
getBrandList()   // X
```

- Raw 값으로부터 enum을 찾을 때 함수 이름은 `find()`로 한다.
```kotlin
enum class Color {
    RED, BLUE, GREEN;

    fun find(rawColor: String): Color = when (rawColor) {
        "red" -> RED
        "blue" -> BLUE
        "green" -> GREEN
        else -> throw IllegalArgumentException("invalid color: $rawColor")
    }
}
```

### Listener
#### Lisetner 이름
- function을 1개만 가진 경우, `fun interface OnXXXXListener`
- function을 2개 이상 가진 경우, `interface XXXListener`
#### `on[명사][동사]()`
- publisher가 이벤트만 전달하고 listener가 전적인 책임을 처리할 때
- 이벤트를 handle하는 주체가 listen하고 있는 곳일때
```kotlin
fun onClick()
fun onFocusChange()
fun onScrollChange()
fun onAnimationStart()
fun onTextChange()
```

#### `on[명사][동사 과거형]()`
- publisher가 무언가를 처리하고 listener에게 알려줄 때
- 어떤 동작을 하고나서 이 동작이 일어났음을 listener에게 알려줄때
- onEach(), doOnXXX() 개념처럼 특정 이벤트를 intercept해서 쓸때
- 동작을 한뒤에 listener를 호출해야 과거형의 이름과 걸맞음
```kotlin
fun onScrollStateChanged()
fun onTextChanged()
```

#### 기타
- Listener하는 곳에서 과거형 여부에 따라서, 그 이벤트에 대한 처리를 해야 하는지 말아야 하는지를 판단가능

## Formatting
### 개행
- 생성자는 한 줄 이상이라면 개행한다.
- 함수는 한 줄에 Parameter 정의가 가능하다면 한 줄로 사용하고, 그렇지 않다면 Parameter 별로 개행한다.

### When Statement
- 한 줄에 들어가는 when 분기는 중괄호를 사용하지 않는다.
```kotlin
when (value) {
    0 -> return
    // ...
}
```

- 여러개의 조건을 동시에 사용하는 경우 `->`를 포함한 블록은 내려서 작성한다.
```kotlin
when (value) {
    foo -> // ...
    bar,
    baz
    -> return
}
```
