# Creating a Question Class

- class 뒤에는 대문자로 표기 (각 widget도 서로 다른 class에 속하기 때문에 대문자로 표기) 
- variables에 value를 주기 위해 **Constructor**를 생성해야 함
* main.dart에 새로운 quesion object 만들기
-> 새로운 object import하기 (import 'question.dart'; 추가)
```dart
class Question {
  String questionText;
  bool questionAnswer;

  Question({String q, bool a}) {
    questionText = q;
    questionAnswer = a;
  }
}
```
* 아래는 Constructor의 예시
```dart
 Question({String q, bool a}) {
    questionText = q;
    questionAnswer = a;
  }
```
* question constructor를 기반으로 새로운 question object 생성하기
```dart
Question q1 = Question(q: 'You can lead a cow down stairs but not up stairs.', a: false);
```
* question과 answer를 하나로 묶어서 표현한 object 만들기 (object를 만들기 위해 class를 만듦)
```dart
List<Question> questionBank = [
    Question(q: 'You can lead a cow down stairs but not up stairs.', a: false),
    Question(
        q: 'Approximately one quarter of human bones are in the feet.',
        a: true),
    Question(q: 'A slug\'s blood is green.', a: true),
  ];
```

# Classes and Objects
* class = blueprint 
* object = car </br>
(앱이 돌아가기 전에, 어떻게 function할지를 정하기 위해 class가 필요함)

## 1. Class
1) **Properties** (or fields) </br>
e.g) color; numberOfSeats;
2) **methods** </br>
e.g) drive(); break();

### Class의 특징
* 대문자로 표현 <-> variable이나 function을 표현할 때는 소문자
* class 안에서 variables는 variables로 불리지 않고 **properties나 fields**로 정의됨 
* class 안에서 function은 function으로 불리지 않고 **method**로 정의됨
```dart
class Car {
  int numberOfSeats = 5; //variable (properties)
  void drive() { //function (method)
    print('wheels start turning');
  }
}
```

## 2. Objects
### Object를 만드는 방법 1
1) class 만들기
2) class로부터 object 만들기 
```dart
Car myCar = Car(); 
// Car=type, myCar=name(실제 object), Car();=이 class의 새로운 버전
```
e.g)

<추가 설명> 
- class로 모든 human은 디폴트 값으로 시작값을 15로 부여한 것임
- 결과값은 15, 20 
```dart
void main() {

  Human jenny = Human();
  print(jenny.height);

  Human james = Human();
  print(james.height);

}

class Human {
  double height = 15;
  int age = 0;
}
```
- 각각의 object가 다른 value를 갖게 하는 방법 : **Constructor**
- class에서 constructor를 만들 때 class에 input을 넣을 수 있음
- dot notation으로 talk method를 트리거할 수 있음
- 결과값: 15, Why is the sky blue
```dart
void main() {
  
  Human jenny = Human(startingHeight: 15);
  print(jenny.height);
  
  jenny.talk('Why is the sky blue'); //dot notation 사용

}

class Human {
  double height;
  int age = 0;
  
  Human({double startingHeight}) {
    height = startingHeight;
  }
  
  void talk(String whatToSay){
    print(whatTosay);
  }
}
```