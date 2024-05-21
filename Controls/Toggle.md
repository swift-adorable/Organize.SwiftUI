
# Toggle

on/off 상태를 처리하는 Toggle에 대해 공부합니다.

```swift
struct Toggle_Tutorials: View {
    @State private var isOn = false
    
    var body: some View {
        VStack(spacing: 30) {
            Image(systemName: isOn ? "lightbulb.fill" : "lightbulb")
                .resizable()
                .foregroundColor(isOn ? .yellow : .gray)
                .shadow(color: .yellow, radius: isOn ? 50 : 0)
                .aspectRatio(contentMode: .fit)
                .frame(width: 300, height: 300)
            
            // #1
            Toggle("Switch", isOn: $isOn)
                .padding()
            
            // #2
            Toggle(isOn: $isOn) {
                Label("Switch", systemImage: "bolt")
            }
            .padding()
            
            // #3
            VStack {
                
                Label("Switch", systemImage: "bolt")
                
                Toggle(isOn: $isOn) {
                    EmptyView()
                }.padding()
                .labelsHidden()
                
            }
            
        }
    }
}
```

