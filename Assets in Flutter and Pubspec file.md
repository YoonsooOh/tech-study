# pubspec.yaml
=Configuration file for flutter project

* 주의사항: Indentation in yaml file (모든 indent는 two spaces)
  
<<<<<<< HEAD
* 왼쪽 바에서 두 칸 간격 뒤에 있는 내용: top level item의 embedded된 children에 해당
=======
* 왼쪽 바에서 두 칸 간격 뒤에 있는 내용: top level item의 enbeded된 children에 해당
>>>>>>> 3090737e1a33365b80e44d07c4fdc89841101393

<예시 코드>

flutter: </br>
  uses-material-design: true </br>
  assets: </br>
     - images/diamond.png

-> assets는 flutter project의 children

-> 이미지가 여러 개 있을 경우, images/ 까지만 입력하면 이미지 파일의 모든 파일을 프로젝트로 통합할 수 있음.

* assets에 있는 이미지 파일을 프로젝트로 통합하려면 packages get 클릭 - run 앱

