
# Alert

경고창을 표시하는 방법을 공부합니다.

```swift
struct  Alert_Tutorials: View {
    @State private var message = ""
    @State private var showAlert = false
    @State private var showImageAlert = false
    @State private var imageData: ImageData? = nil
    var body: some View {
        VStack {
            Text(message)
                .font(.largeTitle)

            Button {
                imageData = ImageData.sample
                showImageAlert = true
                //showAlert = true
            } label: {
                Text("Show Alert")
            }
            .padding()
            .alert("Alert", isPresented: $showImageAlert, presenting: imageData) { data in
                Button("Filter Apply") {
                    message = data.filters.joined(separator: ", ") + " Filter Applying"
                }
                
                Button(role: .cancel) {
                    message = "Cancel!!"
                } label: {
                    Text("Cacnel")
                } 
                
                Button(role: .destructive) {
                    message = "\(data.name) remove"
                } label: {
                    Text("Remove")
                }
                
            } message: { data in
                Text("\(data.name) 파일에서 어떤 작업을 할까요?\n\n촬영 일자: \(data.date)")
            }
        }
    }
}

/*
.alert("Alert", isPresented: $showAlert) {
    Button("OK") {
        message = "OK!!"
    }
    
    Button(role: .cancel) {
        message = "Cancel!!"
    } label: {
        Text("Cacnel")
    }
    
    Button(role: .destructive) {
        message = "remove!!"
    } label: {
        Text("Remove")
    } 
} message: {
    Text("Watch out!!!")
}
 */
```

## Alert

`.alert` Modifier는 연달아 사용 가능하지만 **isPresented** 에 적용 되는 값은 동일 값으로 하면 안된다.
