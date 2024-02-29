
# Confirmation Dialog

Confirmation Dialog를 표시하는 방법에 대해 공부합니다.

```swift
struct  ConfirmationDialog_Tutorials: View {
    @State private var showDialog = false
    @State private var color = Color.black

    var body: some View {
        VStack {
            Spacer()
            
            Circle()
                .frame(width: 200, height: 200)
                .foregroundColor(color)
            
            Spacer()
            
            Button {
                showDialog = true
            } label: {
                Text("Select Color")
            }
            .confirmationDialog("Choice Color", isPresented: $showDialog, presenting: ColorData.samples) { (colors) in
                ForEach(colors) { item in
                    Button(item.title) {
                        color = item.color
                }
            }
            //Button("Red") {
                //color = .red
            //}
            //Button("Green") {
                //color = .green
            //}
            //Button("Blue") {
                //color = .blue
            //}
            //Button(role: .cancel) {
            //} label: {
                //Text("Cancel")
            //}
            //Button(role: .destructive) {
                //color = .black
            //} label: {
                //Text("Destructive")
            //}
            } message: { _ in
                Text("What do u want color?")
            }
        }
    }
}
```

## Confirmation Dialog

**Swift** 에서는 `UIAlertController`를 통해 Action Style을 구분지어 Alert 과 Action Sheet 를 한번에 사용했지만,
**SwiftUI**에서는 `.alert()`으로 Alert, `.confirmationDialog()` 로 Action Sheet 를 구현한다.
