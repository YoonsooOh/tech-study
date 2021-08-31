# Flutter Themes
- [**참고 자료**](https://flutter.dev/docs/cookbook/design/themes)
- 나만의 app에 theme을 **customizing**하고자 할 때 사용

### App theme 만들기
1. material app에 새로운 theme property 생성 (**ThemeData widget** 생성)
```dart
class BMICalculator extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      theme: ThemeData.dark(),  //light는 defauㅣt value
      home: InputPage(),
    );
  }
}
```
2. 나만의 theme data widget 생성

- Themedata class의 다양한 properties : [참고 자료](https://api.flutter.dev/flutter/material/ThemeData-class.html)
- e.g) primaryColor 추가 시, appbar 색상 변경 (scaffold의 body는 포함하지 않음)
- material palette 이외의 색상을 커스터마이징할 경우: free tool [ColorZillar](https://www.colorzilla.com/)
  - 우측 상단의 스포이드로 원하는 색상을 클릭(pick color from page)하여 hex code 따기
  - Color(hex code) 붙여넣기
  - 해시태그를 0xFF로 수정하기
  - [Color class](https://api.flutter.dev/flutter/dart-ui/Color-class.html)
  - [Hexadecimal color](https://stackoverflow.com/questions/22239803/how-does-hexadecimal-color-work)
  - Hex code: #_ _ _ _ _ _ (해시태그+6개 value, 여러 색깔 mixing 조합의 value값) (fully opaque: 0xFF, 나머지 6개 characters: actual 색조 결정)
```dart
//기존
      theme: ThemeData(
primaryColor: Colors.red,
accentColor: Colors.purple,
),
//hex code 입력
      theme: ThemeData(
        primaryColor: Color(0xFF0A0E21),
        accentColor: Colors.purple,
      ),
```
- e.g) scaffold의 body-background color 변경 
```dart
      theme: ThemeData(
        primaryColor: Color(0xFF0A0E21),
        scaffoldBackgroundColor: Color(0xFF0A0E21),
        accentColor: Colors.purple,
      ),
```
[TIPS: documentation에서 ctrl + F로 빠른 검색하기]
- e.g) body의 text color 변경
```dart
      theme: ThemeData(
        primaryColor: Color(0xFF0A0E21),
        scaffoldBackgroundColor: Color(0xFF0A0E21),
        accentColor: Colors.purple,
        textTheme: TextTheme(
          body1: TextStyle(color: Color(0xFFFFFFFF)),
        ),
      ),
```
- e.g) dart theme에서 특정 부분만 변경 시, copyWith 사용
```dart
theme: ThemeData.dark().copyWith(
        primaryColor: Color(0xFF0A0E21),
        scaffoldBackgroundColor: Color(0xFF0A0E21),
        accentColor: Colors.purple,
      ),
```
2-1. 특정 버튼을 새로운 **Theme widget을 만들어 그 안으로 wrapping** 하기 
```dart
      floatingActionButton: Theme(  //widget 이름 => Theme
        data: ThemeData(accentColor: Colors.purple),
        child: FloatingActionButton(
          child: Icon(Icons.add),
        ),
```

### Individual components를 분리하여 dart files 만들기
