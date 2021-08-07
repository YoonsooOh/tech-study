# Container widget = div(layout box)

* Tip:
documentation으로 시작하기
URL: https://flutter.dev/docs/development/ui/widgets

URL: https://flutter.dev/docs/development/ui/widgets/layout

Containers with no children try to be as big as possible

container를 safe area에 넣고자 할 때는 alt+enter>wrap with new widget (widget -> SafeArea로 수정)

예시)

margin: EdgeInsets.fromLTRB(30.0, 10.0, 50.0, 20.0),

margin: EdgeInsets.symmetric(vertical: 100.0, horizontal: 50.0),

margin: EdgeInsets.only(left: 30.0),

padding: EdgeInsets.all(20.0), -> container의 엣지로부터 content 사이의 간격 조정

<정리>
* margin : widget의 바깥 
* padding: widget의 내부
* container는 하나의 child만 가질 수 있음 