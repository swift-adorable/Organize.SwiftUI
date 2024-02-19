
# Scene

Scene의 역할과 상태 처리 방법에 대해 공부

```swift
@main
struct SwiftUIApp: App {
    
    var body: some Scene {
        CustomScene()
    }
}

struct  CustomScene: Scene {
    @Environment(\.scenePhase) private  var  scenePhase
        var body: some Scene {
            WindowGroup {
                ContentView()
            }.onChange(of: scenePhase) { (phase) in
                switch phase {
                case .background:
                    break
                case .inactive:
                    break
                case .active:
                    break
                @unknown  default:
                    break
            }
        }
    }
}
```
- Scene 역할 - Custom Scene 구현 - 상태 처리 방법
## Scene의 역할
- 뷰 계층을 담고 있는 컨테이너
- 플랫폼과 현재 앱 상태에 따라서 뷰 계층을 표시하는 시점, 방식을 자동으로 결정 및 처리 해줌
    - WindowGroup
        - SwiftUI가 제공하는 가장 기본적인 Scene
    - DocumentGroup
        - 문서 기반 앱을 만들때 사용

## Scene의 상태 및 처리 방법
    
- Scene의 상태는 active, inactive, background 가 있다.
    - active: 화면에 표시되어 있는 상태에서 touch와 같은 evnet 처리가 가능한 상태
    - inactive: 화면에 표시되어 있지만 event 처리가 불가능한 상태
    - background: 화면에 표시되지않고 background에 있는 상태
- 화면 상태에 따른 처리를 하고싶다면 Modifier 의 ".onChange()" 를 통해 처리
- 주의 할 점: Scene이 2개 이상 일 경우 하나라도 active 상태가 있다면 active가 리턴 될 수 있음. 즉, 모든 Scene이 inactive 상태일 때만 inactive 리턴한다.
