# Dart-Ternary Operator
- if-else문을 최대한 간결하게 한 문장으로 줄여서 표현할 수 있는 방법
- e.g)
```dart
Condition ? DoThisIfTrue : DoThisIfFalse
```
- if/else문(// 기본, 맨 아랫줄 Ternary Operator 사용)
```dart
void main() {

  bool JackBauerIsAwesome = true;

//  if (JackBauerIsAwesome) {
//    print('That\'s great!');
//  } else {
//    print('Oh no!');
//  }

  JackBauerIsAwesome ? print('That\'s great!') : print('Oh no!');
}
```
- variable의 값
```dart
void main() {

 int myAge = 12;
  
  bool canBuyAlcohol = myAge > 21 ? true : false; //canBuyAlcohol은 variable
  print(canBuyAlcohol);
  
}
```

# Dart - Functions as First Order Objects
- 결과값: 13
```dart
void main() {
  int result = calculator(5, 8, add);
  print(result);
}
//int calculator 대신 Function calculator=도 가능
int calculator(int n1, int n2, Function calculation) {
  return calculation(n1, n2);
}

int add(int n1, int n2) {
  return n1 + n2;
}

int multiply(int n1, int n2) {
  return n1 * n2;
}
```