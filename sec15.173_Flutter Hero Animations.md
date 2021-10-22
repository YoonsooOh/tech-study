# Flutter Hero Animations
- 페이지1과 페이지2의 공통된 elements(이미지나 아이콘 등의)의 변화
  - 필수 요소: shared element가 있어야 함, 지속적인 변화가 있어야 함
- [참고 자료](https://flutter.dev/docs/development/ui/animations/hero-animations)
- hero widget 이용
  - 3 요소:
    1) 2 x hero widgets
    2) 공통의 tag property 
    3) navigator-based screen transitions e.g) push, pop 등
  - 방법(welcome_screen과 이어지는 registration_screen 사이의 번개 모양 animation주기) 
    - 번개 이미지의 container를 새로운 widget으로 wrapping
    - hero widget 만들기
    - tag 추가 (registration_screen도 동일) 
      - tag의 개수는 상관 없음
    ```dart
    Hero( 
              tag: 'logo', /tag 추가
              child: Container(
                height: 200.0, /height가 60에서 200으로 변화
                child: Image.asset('images/logo.png'),
              ),
            ),
    ```
    
---
# Custom Flutter Animations with the Animation Controller
- custom animation 3 요소
  1) Ticker
  2) Animation Controller
  3) Animation Value

```dart
class _WelcomeScreenState extends State<WelcomeScreen>
    with SingleTickerProviderStateMixin {
  AnimationController controller;
  @override
  void initState() {
    super.initState();
    controller = AnimationController( //controller에 해당
      duration: Duration(seconds: 1),
      vsync: this,  //ticker에 해당 
    );
  }
```
- animation이 끝나는 시점을 console에 표시 
```dart
    controller.forward();
    animation.addStatusListener((status) {
      print(status); //표시점 추가 
    });
```
- 시작점과 마지막점의 색을 달리 설정
```dart
void initState() {
    super.initState();
    controller =
        AnimationController(duration: Duration(seconds: 1), vsync: this);

    animation = ColorTween(begin: Colors.blueGrey, end: Colors.white)
        .animate(controller);

    controller.forward();

    controller.addListener(() {
      setState(() {});
      print(animation.value);
    });
```
---
# Prepackaged Flutter Animations
[참고자료](https://pub.dev/packages/animated_text_kit)

- 방법
  1) pubspec yaml에 복붙 후 pub get 클릭
  ```dart
    animated_text_kit: ^1.3.0
  ```
  2) import하기
  ```dart
  import 'package:animated_text_kit/animated_text_kit.dart';
  ```
  3) animatedTextKit로 변경
  ```dart
  TyperAnimatedTextKit(  //기존 Text 
                  text: ['Flash Chat'],  //list []로 감싸기
                  textStyle: TextStyle(  //style -> textStyle로 수정
  ```