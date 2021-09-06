# The GestureDetector widget

- icon card를 클릭하면 background color가 바뀌도록 하는 방법(interactive하게 바꾸는 방법)
1) reusablecard를 GestureDetector로 wrapping하기
2) onTap 추가하기
```dart
Expanded(
                  child: GestureDetector(
                    onTap: () {
                      print('Male card was pressed');
                    },
                    child: ReusableCard(
```
3) inactiveCardColour const 만들기
```dart
class _InputPageState extends State<InputPage> {
  Color maleCardColour = inactiveCardColour;
  Color femaleCardColour = inactiveCardColour;
```
4) updateColour method 만들기
```dart
class _InputPageState extends State<InputPage> {
  Color maleCardColour = inactiveCardColour;
  Color femaleCardColour = inactiveCardColour;

  void updateColour(int gender) {  //method 만들기
    if (gender == 1) {
      if (maleCardColour == inactiveCardColour) {
        maleCardColour = activeCardColour;
      } else {
        maleCardColour = inactiveCardColour;
      }
    }
  }
```
4-1) setState 추가하기
```dart
child: GestureDetector(
                    onTap: () {
                      setState(() {
                        updateColour(1);
                      });
                    },
```
5) 성별 두 버튼이 모두 눌리지 않도록 수정하기
```dart
    if (gender == 2) {
      if (femaleCardColour == inactiveCardColour) {
        femaleCardColour = activeCardColour;
        maleCardColour = inactiveCardColour;  //추가하기
      } else {
        femaleCardColour = inactiveCardColour;
      }
    }
  }
```