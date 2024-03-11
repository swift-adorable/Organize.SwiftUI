
# TextField

TextField로 문자열을 입력받는 방법과 포커스를 제어하는 방법에 대해 공부합니다.
- TextField
- SecureField
- @FocusState

```swift
enum FieldType: Hashable {
    case Email
    case Password
}

struct TextField_Tutorials: View {

    @State private var email: String = ""
    @State private var password: String = ""
    @State private var showJoinAlert = false
    @State private var showInputAlert = false

//  @FocusState private var emailFocused: Bool
//  @FocusState private var passwordFocused: Bool

    @FocusState private var focusedField: FieldType?
    
    var body: some View {
        Form {
            Section {
                //prompt = placeholder
                //TextField("Email", text: $email, prompt: Text("Input Email"))
                TextField("Email", text: $email, prompt: nil)
                    .textInputAutocapitalization(.never) //첫 문자 기본 대문자 해제
                    .disableAutocorrection(true) //자동완성
                    .focused($focusedField, equals: .Email)
                    .submitLabel(.next)
                    .onSubmit {
                        //  passwordFocused = true
                        focusedField = .Password
                    }
                    
                SecureField("Password", text: $password, prompt: nil)
                    .textInputAutocapitalization(.never)
                    .disableAutocorrection(true)
                    .focused($focusedField, equals: .Password)
                    .submitLabel(.done)
                    .onSubmit {
                        if email.isEmpty {
                            showInputAlert = true
                        } else {
                            showJoinAlert = true
                            //  emailFocused = false
                            //  passwordFocused = false
                            focusedField = nil
                        }
                    }
            }
            
            Section {
                Button {
                    if email.isEmpty {
                        showInputAlert = true
                    } else {
                        showJoinAlert = true
                        //  emailFocused = false
                        //  passwordFocused = false
                        focusedField = nil
                    }
                } label: {
                    Text("회원가입")
                }
                .frame(maxWidth: .infinity)
                .alert("회원가입", isPresented: $showJoinAlert) {
                    Button {
                        email = ""
                        password = ""
                    } label: {
                        Text("확인")
                    }
                } message: {
                    Text("계정: \(email)\n비밀번호: \(password)")
                }    
                .alert("경고", isPresented: $showInputAlert) {
                    Button {
                        //emailFocused = true
                        focusedField = .Email
                    } label: {
                        Text("확인")
                    }
                } message: {
                    Text("이메일을 입력해 주세요")
                }
            }
        }
        .onAppear {
            DispatchQueue.main.asyncAfter(deadline: .now()+1) {
                focusedField = .Email
            }
        }
    }
}
```

텍스트필드를 커스터마이징 합니다.
- TextField Style
- Content Type
- Keyboard Type
- Input Format

```swift
struct TextFieldStyles: View {

    @State private var email: String = ""
    @State private var password: String = ""
    @State private var favoriteNumber: Int = 0
    
    var body: some View {
        VStack {
        TextField("Email", text: $email, prompt: Text("Input Email"))
            .padding()
            .textFieldStyle(.roundedBorder)
            .textContentType(.username)
            //.keyboardType(.emailAddress)
            
        SecureField("Password", text: $password, prompt: Text("Input Password"))
            .padding()
            .textFieldStyle(.roundedBorder)
            .textContentType(.password)
            //Password Auto Fill
            
        TextField("Number", value: $favoriteNumber, format: .number)
            .padding()
            .textFieldStyle(.roundedBorder)
            //.keyboardType(.numberPad)
        }
    }
}
```

## Summary
- TextField는 iOS에서 세번째 파라미터 `prompt`는 placeholder로 사용되지만 값이 nil 이면, 첫번째 파라미터 `_ titleKey`가 placeholder로 사용된다. 단, MacOS는 `prompt`를 지정해줘야만 placeholder가 보인다.
- 대표적인 Modifier
    - `.textInputAutocapitalization(.never)` //첫 문자 기본 대문자 해제
    - `.disableAutocorrection(true)` //자동완성 해제
- `TextField`는 일반적인 텍스트 입력에 사용되고, `SecureField`는 보안 관련 정보를 입력받을 때 사용됩니다.
- `submitLabel`, `onSubmit`은 키보드의 return키의 역할 및 액션 지정에 사용된다.
- `UITextContentType` : 텍스트 입력 영역의 의미를 식별하는 상수 (url, identifier, location data 등)
- `TextFieldStyle`: 텍스트 필드의 border 형태 지정 가능
