
# Popover

Popover로 화면을 표시하는 방법을 공부합니다.

```swift
struct Popover_Tutorials: View {
    @State private var popOver = false
    var body: some View {
        Button(action: {
            popOver = true
        }, label: {
            Text("Show Popover")
        })
        .padding()
        .popover(isPresented: $popOver) {
            Form_Tutorials().frame(minWidth: 320, minHeight: 500)
        }
    }
}
```

```swift
struct Form_Tutorials: View {

    @State private var email = ""
    @State private var password = ""
    @State private var address = ""
    @State private var age = 0
    @State private var receiveEmail = false
    
    var body: some View {
        Form {
            Section(content: {
                TextField("Email", text: $email)
                SecureField("Password", text: $password)
                TextField("Address", text: $address)
            }, header: {
                SectionHeaderView(title: "Text Input")
            })
            
            Stepper("Age: \(age)", value: $age)
            
            Toggle(isOn: $receiveEmail, label: { Text("Receive Email") })
            
            Button("확인") {
            }
            .padding()
            .frame(maxWidth: .infinity)
        }
    }
}
```


## Popover

- **Device(Mac Book, iPad, iPhone)의 Screen Size**에 따라 Popover 할 View의 형태가 정해진다.
    - Mac Book이나 iPad의 경우 dropdown menu 처럼 형태가 나오며, iPhone은 modal 형태로 Popover된다.
