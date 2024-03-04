
# Interactive Dismiss

Interactive Dismiss를 제어하는 방법에 대해 공부합니다.

```swift
struct InteractiveDismiss: View {

    @State private var showComposer = false
    @State private var edited = false
    
    var body: some View {
        Button {
            showComposer = true
        } label: {
            Text("Show Me!")
        }
        .padding()
        .sheet(isPresented: $showComposer, onDismiss: nil) {
            ComposeScene(edited: $edited)
                .interactiveDismissDisabled(edited)
        }
    }
}
```

```swift
struct ComposeScene: View {

    @Binding var edited: Bool
    @State private var title: String = ""
    @State private var content: String = ""
    @Environment(\.dismiss) private var dismiss
    
    var body: some View {
        NavigationView {
            Form {
                TextField("Title", text: $title)
                    .onChange(of: title) { _ in
                        edited = title != "" || content != ""
                    }
                TextEditor(text: $content)
                    .onChange(of: content) { _ in
                        edited = title != "" || content != ""
                    }
            }
            .navigationTitle("Compose")
        }
    }
}
```


## Interactive Dismiss
- Modal ViewController가 화면에서 제거되는 방법 중 하나로 사용자가 모달을 제스처로 스와이프 혹은 드래그하여 닫을 수 있게 하는 방법이다.
- **UIKit**의 `UIPresentationController`를 사용하여 이 기능을 구현하며, **SwiftUI**에서는 `.dismissable()` modifier를 사용하여 이러한 Interactive Dismiss를 구현한다.

- **TextField**와 **TextEditor**의 차이
    - 입력해야 할 텍스트의 길이와 형태에 따라 적절한 컴포넌트를 선택한다.
    - TextField
        - `TextField`는 한 줄의 짧은 텍스트를 입력하기 위한 UI를 제공
    - TextEditor
        - `TextEditor`는 여러 줄에 걸쳐 긴 텍스트를 입력하기 위한 UI를 제공
