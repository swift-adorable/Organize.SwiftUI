
# Form

입력화면 구현에 사용하는 Form에 대해서 공부합니다.

```swift
struct  Form_Tutorials: View {
    
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

## Form

SwiftUI에서 Form은 사용자 인터페이스에서 정보를 입력하고 수집하는 데 주로 사용되는 UI 다.
Form은 여러 가지 입력 필드와 다른 유형의 데이터를 사용자에게 표시할 수 있는 구조를 제공하고, 사용자가 데이터를 입력하고 제출할 수 있다.
