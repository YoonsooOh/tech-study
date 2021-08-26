
## Object Oriented Programming
- 4가지 기둥 : 1) Abstraction 2) Encapsulation 3) Inheritance 4) Polymorphism
- e.g) language : Java, Swift, Dart
---
# 1. Abstraction in Action
- 더욱 복잡한 시스템을 만들기 위해 <u>**특정 역할을 갖춘 더 작은 구성**</u>으로 쪼개는 기능 </br>
= functionality를 쪼개서 서로다른 component로 나눈다. (이를 통해 complexity를 manage할 수 있음) 
- abstract = make more modular과 같은 의미
- code base를 보다 reusable하고 modular하게 만들 수 있음. </br>
e.g) main.dart와 분리된 quizBrain을 만듦으로써 quiz brain을 생성하는 class만 수정하여 object를 바꿀 수 있음. 


### sec10_Quizzler
Brain for our quiz이라는 독립된 object를 만들어서 functionality를 abstract함
```dart
//QuizBrain = 새로운 quizbrain object 생성, quizBrain = object의 이름(소문자로 시작) 
QuizBrain quizBrain = QuizBrain();
//questionBank는 quizBrain object의 property가 됨
quizBrain.questionBank[questionNumber].questionText,
```
---
# 2. Encapsulation in Action
Encapsulate하는 방법 : property 앞에 _를 붙여서 property를 private하기 만들기
-> QuizBrain만이 questionBank의 콘텐츠에 접근할 수 있음을 의미
```dart
class QuizBrain {
  List<Question> _questionBank = [
```
---
# 3. Inheritance in Action
- 모든 class는 superclass나 parent class로부터 inherit 받을 수 있음.
- Inheritance는 object를 만들 때 매우 유용함.
- <u>**extend keyword**</u>를 이용하면 parent class의 properties나 methods를 inherit할 수 있음.
- e.g) chef와 pastry chef는 기능적으로 유사한 점이 많지만, 사실상 조금은 다른 일을 하는 것과 같은 상황에서 inheritance 필요 
- parent class와 공통된 코드를 다시 입력하지 않고, **다른 부분만 입력하면 됨.**


< class로부터 object 만드는 code 및 classes object가 작동하는 방법 예시 >
- 결과값: 5, wheels turn.
```dart
void main() {
  
  Car myNormalCar = Car(); //Car class로부터 새로운 object 만들기
  
  print(myNormalCar.numberofSeat);
  
  myNormalCar.drive();
}

class Car {
  int numberofSeat = 5; //properties
  
  void drive() { //methods
    print('wheels turn.');
  }
}
```
< 위의 normal car에서 inherit하여 electric car를 만드는 코드 예시 >
- **extends**를 활용하면 electric car은 디폴트값로 parent class인 car class의 특징을 모두 가질 수 있음.
- parent class와 공통된 부분은 중복해서 코드를 넣지 않아도 됨.
- 결과값: 5, wheels turn., wheels turn.
```dart
void main() {
  
  Car myNormalCar = Car();
  
  print(myNormalCar.numberofSeat);
  
  myNormalCar.drive();
  
  ElectricCar myTesla = ElectricCar();
  
  myTesla.drive();
}

class Car {
  int numberofSeat = 5;
  
  void drive() {
    print('wheels turn.');
  }
}

class ElectricCar extends Car {
  int batteryLevel = 100; //parent class의 코드는 입력하지 않고, ElectricCar만의 property와 method만 입력

  void recharge() {
    batteryLevel = 100;
  }
}
```
---
# 4. Polymorphism in Action
- parent class의 method를 **override**하여 새로운 **나만의 버전 method**를 customizing함.
- 결과값: glide forwards
```dart
void main() {
  
//   Car myNormalCar = Car();
  
//   print(myNormalCar.numberofSeat);
  
//   myNormalCar.drive();
  
//   ElectricCar myTesla = ElectricCar();
  
//   myTesla.drive();
  
//   myTesla.recharge();
  
  LevitatingCar myMagLev = LevitatingCar();
  
  myMagLev.drive();
}

class Car {
  int numberofSeat = 5;
  
  void drive() {
    print('wheels turn.');
  }
}

class ElectricCar extends Car {
  int batteryLevel = 100;
  
  void recharge() {
    batteryLevel = 100;
  }
}

class LevitatingCar extends Car {
  
  @override
  void drive() {
    print('glide forwards');  
  }
  
}
```
- parent class의 특정 부분을 가져와서 add할 수는 있지만 그 이상은 불가능함.
- super을 활용하여 parent class 실행 & 새로운 버전을 실행
- 결과값: wheels turn., steering towards 1 hacker way 
```dart
void main() {
  SelfDrivingCar myWaymo = SelfDrivingCar('1 hacker way');
  
  myWaymo.drive();

}

class Car {
  int numberofSeat = 5;
  
  void drive() {
    print('wheels turn.');
  }
}


class SelfDrivingCar extends Car {
  String destination; //새로운 property인 destination
  
  SelfDrivingCar(String userSetDestination) { //custom constructor: SelfDrivingCar
    destination = userSetDestination; 
  }
  
  @override
  void drive() {
    super.drive(); //superclass의 drive method를 실행
    
    print('steering towards $destination');
  }
  
}
```