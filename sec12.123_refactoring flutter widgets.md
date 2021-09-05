# Extracting and refactoring flutter widgets
- 반복되는 widget 우클릭 후, refactor>extract flutter widget>새로운 이름 설정 
  - widget을 extract해서 분리된 class를 생성할 수 있음.
  - 여러 곳에 반복되는 widget을 일일이 수정할 필요없이, 분리된 class를 다룰 수 있음.
  ###BMI Calculator
- 사용자가 버튼 클릭 시 버튼 색상을 바꾸는 방법(각각의 색상을 다르게 customizing)
1) ReusableCard class에서 property 만들기
2) constructor 만들기
```dart
class ReusableCard extends StatelessWidget {
  ReusableCard(this.colour); 
  //constructor 생성(class의 이름 적고, 괄호 안에 initialize하고자 하는 property 적기)
  //property에 name을 적고자 한다면 ({this.colour})
```
3) ReusableCard 각각에 원하는 color propery를 custom하기 
4) ReusableCard class의 color에는 공통된 color 대신, 새로 만든 colour로 대체
5) ResuableCard widget을 만들 때는 항상 color가 require하기 때문에 this.colour라는 property 앞에 @require 붙이기 
6) property 앞에 final 붙이기
```dart
class ReusableCard extends StatelessWidget {
  ReusableCard({@required this.colour});
  
  final Color colour;
  //final이 colour이라는 property를 immutable하게 만듦(수정할 수 없도록)
```
  ### Key class
- widget의 상태(state)를 추적하고자 할 때 key 사용
- widget tree에서 포지션이 바뀔 때 사용하면 유용함. 아래의 경우를 제외하고 보통은 필요 없음.
- e.g) 애니메이션이나 scrolling on screen과 같이 widget이 스크린에서 물리적으로 움직일 때 주로 발생함.
- [언제, 그리고 왜 key를 사용하는지에 관한 영상 참고 자료](https://www.youtube.com/watch?v=kn0EOS-ZiIc)
---
# [Dart] Final vs Const

- instance variable = instance field = property
- immutable = unchangable (stateless widget에 해당)
- Immutability: 새롭게 업데이트하고자 할 때는 없애고 새롭게 만들어야 함
  - 키워드 final을 property 앞에 넣어서 unchangable하게 만듦 (reusableCard의 color의 final value)
```dart
class ReusableCard extends StatelessWidget {
  ReusableCard({@required this.colour});

  final Color colour;
```
- const: compile-time constant(코드가 compile되었을 때만 가능), runtime에는 불가능
- final: 앱이 돌아갈 때는 언제든 가능
```dart
final int DateTime;  //프로그램 실행 후 시간 받아오게 해주는 api -> runtime에서만
```
- 코드 상단에 const를 따로 만들고, container나 해당 코드를 각각 찾아가서 수정할 필요 없이 위에서 한번에 값을 수정할 수 있음.
```dart
const bottomContainerHeight = 80.0;

~

Container(
color: Color(0xFFEB1555),
margin: EdgeInsets.only(top: 10.0),
width: double.infinity,
height: bottomContainerHeight,  //위에서 만든 const 이름 넣기
)
```

# Creating Custom Flutter widgets
- customizing하기 위한 단계
1) [pub.dev 관련 자료](https://pub.dev/packages/font_awesome_flutter/versions/8.4.0)에서 해당 콘텐츠를 pubspec.yaml에 추가 후, pub.get 클릭
2) input_page.dart에 해당 package import하기
3) 해당 부분 코드 추가
- 예시
```dart
Expanded(
                  child: ReusableCard(
                    colour: Color(0xFF1D1E33),
                    cardChild: Column(
                      mainAxisAlignment: MainAxisAlignment.center,
                      children: [
                        Icon(
                          FontAwesomeIcons.mars,
                          size: 80.0,
                        ),
                        SizedBox(
                          height: 15.0,
                        ),
                        Text(
                          'MALE',
                          style: TextStyle(
                            fontSize: 18.0,
                            color: Color(0xFF8D8E98),
                          ),
                        )
                      ],
                    ),
                  ),
                ),
```
- custom icon content widget을 main tree에서 분리해서 새롭게 만드는 방법
1) extract widget하기
2) 새로 만든 widget(IconContent)에서 새 property 만들기
3) custom constructor 만들어서 해당 part 트리거하기
4) 해당 property가 실제 main build method의 어디에서 나타나는지 구체화하기
5) main tree에서 내용 업데이트하기