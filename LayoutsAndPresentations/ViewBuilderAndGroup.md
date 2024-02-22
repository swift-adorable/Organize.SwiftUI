
# View Builder & Group

ViewBuilder의 역할과 Group으로 뷰를 그룹핑하는 이유에 대해 공부합니다.

```swift
struct  Group_Tutorials: View {
    var body: some View {
        VStack {
            Group {
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
            }.font(.title2)
            
            VStack {
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
                Text("Hello, World!")
            }.padding()
        }
    }
}
```

SwiftUI에서는 Child View의 최대 개수를 10개로 제한하고 있다. 아래 VStack의 initializer를 보자.
`@ViewBuilder`라는 특성이 있는데, 하나의 **closure**에서 여러개의 Child View를 나열할 수 있게 해주는 특성이 있다. 

```swift
    ///  - **Parameters**:
    ///  - alignment: The guide for aligning the subviews in this stack. This guide has the same vertical screen coordinate for every subview.
    ///  - spacing: The distance between adjacent subviews, or `nil` if you want the stack to choose a default distance for each pair of subviews.
    ///  - content: A view builder that creates the content of this stack.
    
    ///  - **Initializer**
    @inlinable public init(alignment: HorizontalAlignment = .center, spacing: CGFloat? = nil, @ViewBuilder content: () -> Content)
    
```

## @ViewBuilder

- `@ViewBuilder`는 내부적으로 `buildBlock()`이라는 Method를 호출한다.
- 보통 `Section`이나 `Stack` 같은 View로 다른 View를 감싸지만, 내부의 View Layout에 영향을 주지만, `Group`으로 감싸면 영향을 주지 않는다.
- `Group` modifier를 통해 어떠한 Layout 특성을 변경한다면 내부의 View들의 Layout이 같이 변경되지만, `Section`이나 `Stack`은 자신만의 Layout 특성을 가지고 있기 때문에 내부의 View가 아닌 자기 자신의 Layout이 변경된다.
