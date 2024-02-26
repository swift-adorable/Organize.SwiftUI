
# Overlay

뷰 위에 새로운 뷰를 추가하는 overlay에 대해 공부합니다.

```swift
struct  Overlay: View {
    @State var selected = false
    
    var body: some View {
        EmojiView(emoji: "😎")
            .overlay(alignment: .bottomTrailing) {
                if selected {
                    Image(systemName: "checkmark.circle.fill")
                        .foregroundColor(.blue)
                        .font(.largeTitle)
                }
            }
            .onTapGesture {
                selected.toggle()
            }
            //#2
            //.overlay {
            //    Image("big-photo").resizable()
            //}
            //#1
            //.overlay(.thickMaterial, in: Circle())
            //.opacity(0.3)
    }
}
```

## Overlay

`ZStack`으로도 Overlay 효과(?)를 구현이 가능하지만, Layout을 구성하는데 있어서 `.overlay` Modifier가 훨씬 용이 할 수 있다.
