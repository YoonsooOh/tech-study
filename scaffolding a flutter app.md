# scaffold class
code를 층별로 나눠서 보도록 나누는 팁:

 setting>editor>general>appearance>'show closing labels in dart source code'

scaffolding(appBar: ) ->scaffold의 한 가지 특성으로 앱바 설정

   1. Property: AppBar

1-1. AppBar widget에는 title(text widget), backgroundcolor라는 widget 두 가지 property 생성 

참고 URL: https://material.io/design/color/the-color-system.html#tools-for-picking-colors

ex. backgroundColor: Colors.blueGrey[900]

2. body

image class 참고 URL: https://api.flutter.dev/flutter/dart-ui/Image-class.html

* networkimage: url은 single quote를 양쪽에 붙여서 작성

*이미지를 정중앙에 배치하려면 image widget을 center widget안에 넣어준다.

1번째 방법: Center(
   child: ~)

2번째 방법: enbed하고 싶은 코드 부분에 alt + enter - center widget

