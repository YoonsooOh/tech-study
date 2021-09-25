# Dart Enums
- 숫자를 이용하지 않고 **의미가 있는 이름**을 부여(Booleans: on/off, True/False처럼 두개의 선택지 위에 다양한 옵션 존재)
- **다수의 옵션이 있을 경우 매우 유용함**
- e.g) carType.convertible, carType.SUV, carType.hatchback
- Enums 예시
```dart
//EnumName은 class name과 같이 대문자로 시작
enum EnumName {typeA, typeB, typeC}

//enum 사용 시
EnumName.typeA
```

- enum 사용 예시
```dart
void main() {

  Car myCar = Car(carStyle: CarType.convertible);
  
}

class Car {
  
  CarType carStyle;
  car({this.carStyle});
}

enum CarType {
  hatchback,
  SUV,
  convertible,
  coupe,
}
```