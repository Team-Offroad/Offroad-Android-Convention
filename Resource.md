# Resource

## Drawable
- `<WHAT>_<WHERE>_<DESCRIPTION>(_<SIZE>)`
- 이미지의 크기가 1개밖에 없는 경우, `<SIZE>`는 생략 가능하다.

### What
| Prefix | 설명 |
| ------------- | ------------- |
| `btn_` | 버튼으로 쓰이는 이미지 |
| `ic_` | 버튼이 아닌 화면에 보여지는 이미지 |
| `bg_` | 버튼이 아닌 화면에 보여지는 이미지 |
| `img_` | 실제사진이거나 아이콘형태가 아닌 일러스트형태의 이미지 |
| `div_` | divider로 활용되는 이미지 |

### Selector
- 배경이나 버튼에서 View의 상태에 따라서 drawable이 변해야 하는 경우에 대한 이름은 아래와 같다.

| 상태 | Suffix |
| ------------- | ------------- |
| Normal | `_normal` |
| Pressed | `_pressed` |
| Focused | `_focused` |
| Disabled | `_disabled` |
| Selected | `_selected` |

### Background
- 배경색이 pressed상태에 따라서 white -> sky_blue로 변하는 경우는 `bg_white_to_sky_blue.xml`로 한다.
- 배경이 white색의 24dp로 테두리를 그리는 경우는 `bg_white_radius_24dp.xml`로 한다.
- 배경이 투명하며 배경의 선만을 sky_blue색의 8dp로 테두리를 그리는 경우는 `bg_stroke_sky_blue_radius_8dp.xml`로 한다.

### 기타
- `img_xxx`의 경우 파일의 크기가 큰경우가 많으므로 [tinypng](https://tinypng.com/)에서 파일크기를 줄인뒤에 추가 해주어야 한다.
- GitHub [imgbot](https://github.com/marketplace/imgbot)을 사용한다면 생략 가능하다.


### 예시
- `btn_call_normal.png`: 전화걸기 버튼 이미지
- `btn_call_pressed.png`: 전화걸기 버튼 눌렸을때의 이미지
- `btn_call.xml`: 전화걸기 버튼 이미지의 selector xml
- `ic_dealer_gift.png`: 딜러가 보내준 기프티콘을 보여줄때 표시되는 이미지
- `img_splash_chart.png`: 스플래시 화면에서 보여지는 차트 이미지

## String
- `<WHERE>_<DESCRIPTION>`
- 특정화면에서 쓰이는 텍스트 아니라 여러군데에서 공통으로 재사용될 텍스트라면 `all_<DESCRIPTION>`로 이름을 짓는다

### 예시
- `permission_dialog_camera_title`: 카메라권한을 요구하는 Dialog의 제목
- `permission_dialog_camera_description`: 카메라권한을 요구하는 Dialog의 설명내용
- `all_yes`: 네
- `all_ok_understand`: 여러 Dialog에서 `네, 알겠습니다`로 쓰이는 공통의 텍스트

## Theme/Style
- Theme는 `theme.xml`, Style은 `style.xml`에 추가한다.
- 1번만 쓰이는 경우에는 style을 만들지 않는다.
  (단, 앞으로 재사용될 가능성이 높은 경우에는 가능)
- 모든 style은 parent를 갖는다.

### Naming
- style의 이름은 parent의 이름패턴과 맞춘다
```xml
<style name=”Widget.HeyDealer.Button” parent=”@style/Widget.AppCompat.Button”>
...
</style>
```
- parent에서 일부 내용만 수정하고자 하는경우, parent이름 뒤에 달라진 내용의 내용을 추가해준다
```xml
<style name="Theme.HeyDealer.Transparent" parent="Theme.HeyDealer">
...
</style>
```
- Base Style과 Theme의 경우는 앞에 `Base`를 붙인다.
```xml
<style name="Base.Theme" parent="..." />
<style name="Base.Theme.Transparent">...</style>
<style name="HeyDealerTheme" parent="Base.Theme">...</style>
<style name="HeyDealerTheme.Transparent" parent="Base.Theme.Transparent" />

<style name="Base.TextAppearance.HeyDealer" parent="...">...</style>
<style name="Base.TextAppearance.HeyDealer.Headline">...</style>
<style name="TextAppearance.HeyDealer.Headline1" parent="Base.TextAppearance.HeyDealer.Headline">...</style>
<style name="TextAppearance.HeyDealer.Headline2" parent="Base.TextAppearance.HeyDealer.Headline">...</style>
```
