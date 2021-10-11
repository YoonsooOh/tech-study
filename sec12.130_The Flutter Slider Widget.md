# The Flutter Slider Widget
- 새로운 constants dart file 만들기
  1. 흩어져 있던 constants를 하나의 파일로 합치기 
  2. 각 파일에 constants import하기
- naming convention
  - constants는 주로 K로 네이밍함 (해당 constant가 들어가 있는 모든 위치에 refactor됨)
```dart
//기존
const bottomContainerHeight = 80.0;
//refactor > rename
const KBottomContainerHeight = 80.0;
```
- slider 생성
```dart
child: Slider(
value: height.toDouble(),
min: 120.0,
max: 220.0,
onChanged: (double newValue) {
setState(() {
height = newValue.round();
});
},
),
```