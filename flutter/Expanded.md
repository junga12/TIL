# Expanded

## 문제 

화면을 구성할 때, 세로로 위젯을 배치하고 싶어서 Column을 생각했었는데  
아래와 같이 두 개의 위젯을 children으로 가지니까 에러가 발생했음.  
에러 내용을 저장해둔게 없지만, 픽셀 오버플로우 에러라고 해서 지정된 영역을 넘어가면 발생하는 에러임  
```dart
body: Column(
          children: <Widget>[
            _c1,
            _c2,
          ],
        )
```

<br>
Column 대신 Stack을 사용해 봤지만 자식으로 가진 두 개의 위젯이 겹치는 문제 발생  

---
그래서 Column을 사용하고, _c1을 Expanded라는 위젯으로 감싸줘서 해결함 

```dart
body: Column(
          children: <Widget>[
            _c1,
            _c2,
          ],
        )
```
---

## Expanded 란?
```dart 
class Expanded extends Flexible {
  const Expanded({
    Key? key,
    int flex = 1,
    required Widget child,
  }) : super(key: key, flex: flex, fit: FlexFit.tight, child: child);
}
```

child의 위젯을 가능한 공간에 채우는 위젯이라고 함.  
즉, 맨 처음에 발생한 픽셀 오버플로우 에러를 처리하기 위해서 Expanded를 사용하면 됨. 가능한 공간에 위젯을 배치하기 때문에 지정된 공간을 넘어갈 일이 없어짐  
