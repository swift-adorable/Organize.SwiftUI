  
# Modifier

Modifier의 공통적인 특징에 대해 공부합니다.

```swift
struct  ContentView: View {

    @State private var value: Double = 0
    
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
    }
}
```

## Modifier
    
- 화면의 Life Cycle 시점에서의 작업을 하고 싶다면 Swift는 UIKit의 viewDidAppear 같은 메소드를 오버라이딩 해서 구현하지만 SwiftUI는 Modifier를 통해 구현
    - `.onAppear { //viewDidAppear와 같은 개념 }`
    - `.onDisappear { //viewDidDisappear와 같은 개념 }`

- 뷰의 모양, 크기, 색상 등을 변경하는 데 사용하며, 자주 사용되는 Modifier의 예시
    1. **크기와 위치**: `frame()`, `padding()`, `position()`
    2. **모양과 모양**: `cornerRadius()`, `border()`, `shadow()`
    3. **색상**: `foregroundColor()`, `backgroundColor()`
    4. **폰트와 텍스트 스타일**: `font()`, `fontWeight()`, `fontStyle()`
    5. **레이아웃**: `alignment()`, `spacing()`, `offset()`
    6. **애니메이션**: `animation()`

- 모든 Modifier는 View를 리턴하므로 Chaining이 가능하다. (순서가 중요!)
