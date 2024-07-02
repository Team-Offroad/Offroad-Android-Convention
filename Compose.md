# Compose

## Layout

### `Spacer()` vs `Modifier.padding()` 사용 기준
- `Column()` `Row()`와 같이 Linear 형태의 Layout에서 margin 개념이면 `Spacer()`를 사용한다.
```kotlin
Column {
    Title()
    Spacer(modifier = Modifier.height(8.dp))
    Content()
}
```
- 그 외는 `Modifier.padding()`을 사용한다.

## Etc
- [Androidx Compose API Guidelines](https://github.com/androidx/androidx/blob/androidx-main/compose/docs/compose-api-guidelines.md)를 준수하고, 예외사항이 발생할 경우 이 페이지를 수정한다.
