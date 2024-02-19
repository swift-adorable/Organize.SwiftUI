
# App

프로젝트 구조와 App 프로토콜의 역할에 대해 공부

```swift
class  Model: ObservableObject { }

@main
struct SwiftUIApp: App {
    @StateObject private var model = Model()
    
    @UIApplicationDelegateAdaptor(AppDelegate.self) var  appDelegate
    
    var body: some Scene {
        WindowGroup {
            ContentView()
                .environmentObject(model)
        }
    }
}

class AppDelegate: NSObject, UIApplicationDelegate {
    //새로운 파일에서 생성한다.
    //NSObject나 UIResponder를 상속 받아야 함.
    //원하는 Method를 구현
}
```

## @main

- App Protocol을 준수하는 구조체나 클래스에 부여하며, compiler가 `main()` 함수를 자동으로 합성한다.
- 앱을 실행할 때 OS 가 가장 먼저 실행하며, 플랫폼에 적합한 방식으로 초기화 과정을 담당

## App Protocol

- main 
    - `main()`의 기본 구현을 제공
- body
    - 화면을 표시 담당
    - body에서 리턴하는 객체는 Scene Protocol을 구현해야 한다
- Application Level에서 데이터를 전달 할 수 있는 방법 2가지
    - instance를 하나 만들어 **.environmentObject** 와 **생성자**를 통해 데이터 전달 가능
    - SwiftUI는 **App Delegate**를 자동으로 생성하지 않는다. (단, **Push Notification**을 구현하려면 반드시 App Delegate를 생성해 연결해야 함!)
