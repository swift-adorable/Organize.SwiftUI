
# Progress View

작업의 진행 상태를 표시하는 ProgressView에 대해 공부합니다.

- Circular Style Progress View
- Linear Style Progress View

```swift
struct ProgressView_Tutorials: View {
    @State private var downloading = false
    @State private var progress: CGFloat = 0.0
    
    @State private var timer: Timer?
    
    var body: some View {
        VStack(spacing: 100) {
            Spacer()
            
            //# 01 - Circular Style Progress View
//            if downloading {
//                ProgressView()
//                    .scaleEffect(2, anchor: .center)
//                    .tint(.black)
//            }
            
            //# 02 - Linear Style Progress View
            ProgressView(value: progress) {
                Label("Download", systemImage: "icloud.and.arrow.down")
            } currentValueLabel: {
                HStack {
                    Spacer()
                    Text("\(progress)")
                }
                
            }
            .tint(.green)
            .padding()
            
            Spacer()
            
            Button("Download") {
                downloading = true
                
                timer?.invalidate() // Cancel any existing timer
                timer = Timer.scheduledTimer(withTimeInterval: 1.0, repeats: true) { timer in
                    if progress < 1.0 {
                        progress += 0.2
                    } else {
                        timer.invalidate()
                        downloading = false
                        progress = 0.0
                    }
                }
                
                DispatchQueue.main.asyncAfter(deadline: .now() + 5) {
                    timer?.invalidate()
                    downloading = false
                    progress = 0.0
                }
                
            }
            .buttonStyle(.borderedProminent)
            .overlay {
                //overlay를 통해 버튼의 탭을 막아주는 효과도 있다.
                if downloading {
                    HStack {
                        ProgressView()
                            .tint(.white)
                    }
                    .frame(maxWidth: .infinity, maxHeight: .infinity)
                    .background(.ultraThinMaterial)
                    .clipShape(RoundedRectangle(cornerRadius: 8))
                }
            }
        }
    }
}
```

## Summary
 - Progress View `init(value: V?, total: V = 1.0, @ViewBuilder label: () -> Label, @ViewBuilder currentValueLabel: () -> CurrentValueLabel)`
    - value의 타입은 바인딩이 아니다. slider는 drag를 통해 값을 직접 바꿀 수 있지만 Progress View는 그냥 보여주기만 하므로 바인딩 형태로 전달 하는게 아니다.
