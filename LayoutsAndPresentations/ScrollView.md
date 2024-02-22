
# ScrollView

일반 뷰에 스크롤 기능을 추가하는 ScrollView에 대해 공부합니다.

```swift
struct  ScrollView_Tutorials: View {
    var body: some View {
        ScrollView([.horizontal, .vertical]) {
            BigPhotoView()
        }.ignoresSafeArea()
    }
}

struct  BigPhotoView: View {
    var body: some View {
        Image("big-photo")
    }
}
```

```swift
///  - **Parameters**:
///  - axes: The scroll view's scrollable axis. The default axis is the vertical axis.
///  - showsIndicators: A Boolean value that indicates 
                    whether the scroll view displays the scrollable component of the content offset, 
                    in a way suitable for the platform. 
                    The default value for this parameter is `true`.
///  - content: The view builder that creates the scrollable view.

///  - **ScrollView Initializer**
public init(_ axes: Axis.Set = .vertical, showsIndicators: Bool = true, @ViewBuilder content: () -> Content)
```

## ScrollView의 특징

- SwiftUI가 제공하는 대부분의 View는 Scroll을 지원하지 않는다. 화면 밖을 벗어나는 View는 Clipping 된다.
- Scroll의 axis, indicators hidden은/는 `init()` Method를 통해 설정한다.
- axis의 default는 **vertical**, showIndicators의 default는 **true** 다.
