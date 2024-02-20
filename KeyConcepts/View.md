
# View

View의 역할과 동작 방식에 대해 공부합니다.

```swift
struct  ContentView: View {

    @State private var randNo = "0"
    
    var body: some View {
        VStack {
            Text(data)
                .padding()
                .font(.largeTitle)
            
            Button {
                randNo = "\(Int.random(in: 1 ... 100))"
            } label: {
                Text("Random Number")
            }
        }
        .onAppear {
            //viewDidAppear와 같은 개념
        }
        .onDisappear {
            //viewDidDisappear와 같은 개념
        }
    }
}
```

## View Protocol
View 는 UI를 구성하는 가장 기본적인 요소
- UIKit의 View는 class로 구현하며 상속 받는 멤버가 많아 SwiftUI에 비해 상대적으로 무거움
- 값 형식으로 구현하기 때문에 레퍼런스 카운팅같은 오버헤드가 없음
- 가볍고 레이아웃 성능이 높음.
-  뷰를 잘게 쪼개서 구현하고 여러 단계로 중첩해 구현하더라도 런타임 오버헤드가 없음.
- 기본적으로 화면 중앙을 기준으로 배치하지만 Swift는 왼쪽 상단을 기준으로 배치
