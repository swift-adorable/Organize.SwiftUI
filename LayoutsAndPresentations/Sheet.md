
# Sheet

새로운 화면을 모달 방식으로 표시하는 방법을 공부합니다.

- Card Modal 
- Fullscreen Modal

```swift
struct Sheet_Tutorials: View {

    @State private var presentCardModal = false
    @State private var presentFullScreen = false

    @State private var imageData: ImageData? = nil

    var body: some View {
        VStack {
            Button {
                //presentCardModal = true
                imageData = ImageData(name: "logo", filters: [], date: .now)
                
            } label: {
                Text("Card Modal")
            }
            .padding()
            //#1
            //.sheet(isPresented: $presentCardModal) {
            //
            //} content: {
            //    ImageScene(presentModal: $presentCardModal)
            //}
            .sheet(item: $imageData, onDismiss: {}) { imageData in
                OptionalImageScene(imageData: imageData)
            }
            Button {
                presentFullScreen = true
            } label: {
                Text("Fullscreen")
            }
            .padding()
            .fullScreenCover(isPresented: $presentFullScreen) {
            
            } content: {
                ImageScene(presentModal: $presentFullScreen)
            }
        }
    }
}
```

```swift
//MARK: Image Scene
struct ImageScene: View {
    //#1
    //@Environment(\.presentationMode) var presentationMode
    //#2
    //@Environment(\.dismiss) var dismiss
    @Binding var presentModal: Bool
    
        var body: some View {
            Image("big-photo")
                .resizable()
                .aspectRatio(contentMode: .fill)
                .ignoresSafeArea()
                .overlay(alignment: .top) {
            Button {
                //#1
                //presentationMode.wrappedValue.dismiss()
                //#2
                //dismiss()
                presentModal = false
            } label: {
                Image(systemName: "x.circle")
                    .resizable()
                    .frame(width: 50, height: 50)
                    .foregroundColor(.white)
                    .padding()
            }
        }
    }
}
```


## Sheet

- **Swift** 에서는 `UIModalPresentationStyle` 를 통해서 ViewController의 Modal 방식을 지정하고,
**SwiftUI**에서는 `.sheet()`로 Sheet 형태, `.fullScreenCover()` 로 Full Screen 형태를 구현한다.
- Modal Presentation을 할 때, `Boolean` or `Identifier` 를 파라미터로 활용한다.
    - Boolean의 **true** or **false**
    - Identifier 값의 존재 여부 **not nil** or **nil**
- 화면을 닫는 방법의 종류
    - @Environment `\.presentationMode` 변수
    - @Environment `\.dismiss` 변수
    - Parent View의 변수를 복사가 아닌 참조를 받게 끔 Binding 하여 사용
        - Preview에 정의 해야하는데 정적 Binding 해서 초기화해준다.
