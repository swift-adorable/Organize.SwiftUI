
# View

View의 역할과 동작 방식에 대해 공부합니다.

```swift
struct  ContentView: View {

    @State private var value: Double = 0
    @State private var randNo = "0"
    
    var body: some View {
        VStack {
            Text("Padding First, Background Second")
                .padding()
                .background(.gray)
            Text("Background First, Padding Second")
                .background(.gray)
                .padding()
            Text("Hello, world \(randNo)!")
                .padding()
                .font(.footnote)
                .foregroundColor(.white)
                .background(.black)
                .border(.gray, width: 2)
                Button {
                    randNo = "\(Int.random(in: 1 ... 100))"
                } label: {
                Text("Random Number")
                    .foregroundColor(.black)
                    .background(.bar)
                }.padding(.bottom, 10)
                Text("\(value)")
                Slider(value: $value)
                    .padding(.horizontal)
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

## Modifier
    
- 화면의 Life Cycle 시점에서의 작업을 하고 싶다면 Swift는 UIKit의 viewDidAppear 같은 메소드를 오버라이딩 해서 구현하지만 SwiftUI는 Modifier를 통해 구현
    - `.onAppear { //viewDidAppear와 같은 개념 }`
    - `.onDisappear { //viewDidDisappear와 같은 개념 }`

- 뷰의 모양, 크기, 색상 등을 변경하는 데 사용하며, 자주 사용되는 Modifier의 예시
        1.  **크기와 위치**: `frame()`, `padding()`, `position()`
        2.  **모양과 모양**: `cornerRadius()`, `border()`, `shadow()`
        3.  **색상**: `foregroundColor()`, `backgroundColor()`
        4.  **폰트와 텍스트 스타일**: `font()`, `fontWeight()`, `fontStyle()`
        5.  **레이아웃**: `alignment()`, `spacing()`, `offset()`
        6.  **애니메이션**: `animation()`

- 모든 Modifier는 View를 리턴하므로 Chaining이 가능하다. (순서가 중요!)
