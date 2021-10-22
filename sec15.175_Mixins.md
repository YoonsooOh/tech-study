# [Dart] Mixins
- 의미: 한 class의 코드를 여러 class에서 '재사용'하는 방식
- 특징: 크고 복잡한 모듈에서 여러 개의 class를 만들고, 그 안에서 수정이 필요할 때 유용함
- e.g)

```dart
void main() {
  Animal().move();
  Fish().move();
  Bird().move();
  Duck().move();  //mixin 사용 시, move 외에 fly, swim 모두 가능 
}

class Animal {
  void move() {  //method
    print('changed position');
  }
}

class Fish extends Animal {  //Animal class를 inherit함 = Animal class의 모든 속성을 모두 가져옴
  @override  //move method의 parent version을 override함
  void move() {
    super.move();
    print('by swimming');
  }
}

class Bird extends Animal {
  @override  //move function의 parent version을 override함
  void move() {
    super.move();
    print('by flying');
  }
}
//flying과 swimming을 모두 가져와야 하는 경우-하나의 class만 inherit가능(하나의 class만 extends 가능)
class Duck extends Animal {
  
}
```

- mixin 사용

```dart
mixin CanSwim {
  void swim() {
    print('changing position by swimming');
  }
}

mixin CanFly {
  void fly() {
    print('changing position by flying');
  }
}

class Duck extends Animal with CanSwim, CanFly { 
  
}
//Animal을 inherit할 필요도 없음(필수x)
class Duck with CanSwim, CanFly {

}
```