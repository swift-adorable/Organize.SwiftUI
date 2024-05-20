
# Button

버튼에서 탭 이벤트를 처리하는 방법과 커스터마이징에 대해 공부합니다.

```swift
struct Button_Tutorials: View {

    @State private var value = Int.random(in: 1...100)
    
    var body: some View {
    
        VStack {
            Spacer()
            
            Text("Random Number")
                .font(.largeTitle)
    
            Text("\(value)")
                .font(.system(size: 200))
        
            Spacer()
    
            // #1
            Button {
                generate()
            } label: {
                Image(systemName: "repeat")
                Text("Generate")
            }
            .padding()
            .background(.blue)
            .foregroundColor(.white)
            .cornerRadius(20)
            
            //버튼 타이틀이 단순 텍스트 인 경우
            Button("Generate", action: generate)
                .padding()
        }
        .frame(maxWidth: .infinity, maxHeight: .infinity)
    }

    private func generate() {
        value = Int.random(in: 1...100)
    }

}
```

Button Styles Example

```swift
struct ButtonStyles: View {

    var body: some View {
    
        VStack {
            Button("Automatic", action: {})
                .padding()
                .buttonStyle(.automatic)
                
            Button("Plain", action: {})
                .padding()
                .buttonStyle(.plain)
                
            Button("Bordered", action: {})
                .padding()
                .buttonStyle(.bordered)
                
            Button("Bordered Prominent", action: {})
                .padding()
                .buttonStyle(.borderedProminent)
                //.buttonBorderShape(.roundedRectangle)
                
            Button("Borderless", action: {})
                .padding()
                .buttonStyle(.borderless)
            
        }
        .tint(.yellow)
    }
}
```
