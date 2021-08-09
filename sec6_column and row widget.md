# Column and row widget
multi-child layout 

child: Column(
            verticalDirection: VerticalDirection.down,

            -> 위에서 아래로

child: Column(
            verticalDirection: VerticalDirection.up,

            -> 아래에서 위로

child: Column(
            mainAxisAlignment: MainAxisAlignment.start,

            -> 가장 윗 라인에 맞추기

child: Column(
            mainAxisAlignment: MainAxisAlignment.end,

            -> 가장 아래 라인에 맞추기

child: Column(
            mainAxisAlignment: MainAxisAlignment.center,

            -> 정중앙 라인에 맞추기

child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,

            -> childeren 간의 간격 고르게 띄어서 출력

child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,

            -> 첫 라인, 마지막 라인, 정가운데 출력

child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,

            -> children의 가로 길이가 가장 길게

