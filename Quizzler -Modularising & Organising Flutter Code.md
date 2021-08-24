# Building a Score Keeper

- 사용자가 몇 개의 문제를 맞추고 틀리는지 추적하는 기능
``` dart
Row(
          children: [
            Icon(
              Icons.check,
              color: Colors.green,
            ),
            Icon(
              Icons.close,
              color: Colors.red,
            ),
```
- rows와 columns는 여러 개의 widget을 포함할 수 있음
- e.g) **column**은 3개의 expanded widget과 1개의 row widget을 가지고, row는 5개의 icon widget을 가짐
- safearea, padding widget, center widget은 1개의 child만 가질 수 있음
- column widget은 list의 형태로 children을 가질 수 있음 (list는 여러 개를 그룹핑할 수 있는 방법)

### list 만드는 방법
``` dart
class _QuizPageState extends State<QuizPage> {
  List<Icon> scoreKeeper = [
    Icon(
      Icons.check,
      color: Colors.green,
    ),
```

# Dart Lists
- index는 0부터 시작
```dart
void main() {
  List<String> myList = [
    'Angela',
    'James',
    'Katie',
    'Jack',
  ];
  
  print(myList[3]);
}
```
-> Jack
```dart
void main() {
  List<String> myList = [
    'Angela',
    'James',
    'Katie',
    'Jack',
  ];
    
  print(myList.indexOf('Katie'));
}
```
-> 2

- list에 추가하는 방법1 (list의 가장 마지막 끝에 추가)
```dart
void main() {
  List<String> myList = [
    'Angela',
    'James',
    'Katie',
    'Jack',
  ];
    
  myList.add('Ben');
  print(myList);
}
```
-> [Angela, James, Katie, Jack, Ben]

- list에 추가하는 방법2 (list의 중간에 insert하기)
```dart
void main() {
  List<String> myList = [
    'Angela',
    'James',
    'Katie',
    'Jack',
  ];
    
  myList.insert(2, 'Ben');
  print(myList);
}
```
-> [Angela, James, Ben, Katie, Jack]

### 실행 이전 또는 이후로 돌아가는 방법
경로: git - VCS operations - show history - 해당하는 타임라인 선택 후 좌상단 REVERT 버튼 클릭

### 리스트 안에서의 위치를 추적하기 위한 variable
```dart
int questionNumber = 0;
```
---
# Checking User Answers

1) 새 variable 생성

boolean(data type)
```dart
onPressed: () {
                //The user picked false.
                bool correctAnswer = answers[questionNumber];
```
2) if~ 코드는 questionNumber를 올리기 전에 나와야 함
```dart
if (correctAnswer == false) {
                  print('user got it right!');
                } else {
                  print('user got it wrong');
                }
                setState(() {
                  questionNumber++;
```

# Dart Conditionals - IF/ELSE
1) == (**equal**) / != (**not equal**) / && (**and**)

2) if절
```dart
if (track == 'clear'){go();}
```
-> ()사이: condition, {}사이: instruction

3) if-else절
```dart
if (track == 'clear'){
  goStraight();
} else {
  turnRight();
}
```

4) Love Calculator
```dart
import 'dart:math';

void main() {
  loveCalculator();

}

void loveCalculator(){
  
  int loveScore = Random().nextInt(100) + 1;
  print(loveScore);
  
  if (loveScore > 70) {
    print('You love each other like Kanye loves Kanye.');
  } else {
    print('You like each other');
  }
}
```
5) else if절

else if절은 여러 개 가능
```dart
import 'dart:math';

void main() {
  loveCalculator();

}

void loveCalculator(){
  
  int loveScore = Random().nextInt(100) + 1;
  print(loveScore);
  
  if (loveScore > 70) {
    print('You love each other like Kanye loves Kanye.');
  } 
  else if (loveScore > 50) {
    print('You like each other');
  }
  else {
    print('You don\'t like each other');
  }
}
```