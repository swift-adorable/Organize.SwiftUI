
# Slider

Slider를 사용해서 드래그로 값을 선택하는 방법을 공부합니다.

```swift
struct Slider_Tutorials: View {
    @State private var r = 0.0
    @State private var g = 0.0
    @State private var b = 0.0
    
    @State private var dragging = false
    
    var color: Color {
        Color(red: r / 255, green: g / 255, blue: b / 255)
    }
    
    var body: some View {
        VStack {
            Button("Reset") {
                r = 0.0
                g = 0.0
                b = 0.0
            }
            .buttonStyle(.borderedProminent)
            .disabled(dragging)
            
            Image(systemName: "umbrella.fill")
                .resizable()
                .foregroundColor(color)
                .frame(width: 250, height: 250)
            
            VStack {
                // # Red
                Slider(value: $r, in: 0 ... 255, step: 1) {
                    EmptyView()
                } minimumValueLabel: {
                    Text("Red").foregroundColor(.red)
                        .frame(width: 60)
                } maximumValueLabel: {
                    Text("\(Int(r))")
                        .frame(width: 60)
                } onEditingChanged: { editing in
                    dragging = editing
                }.padding()
                .tint(.red)
                
                // # Green
                Slider(value: $g, in: 0 ... 255, step: 1) {
                    EmptyView()
                } minimumValueLabel: {
                    Text("Green").foregroundColor(.green)
                        .frame(width: 60)
                } maximumValueLabel: {
                    Text("\(Int(g))")
                        .frame(width: 60)
                } onEditingChanged: { editing in
                    dragging = editing
                }.padding()
                .tint(.green)
                
                // # Blue
                Slider(value: $b, in: 0 ... 255, step: 1) {
                    EmptyView()
                } minimumValueLabel: {
                    Text("Blue").foregroundColor(.blue)
                        .frame(width: 60)
                } maximumValueLabel: {
                    Text("\(Int(b))")
                        .frame(width: 60)
                } onEditingChanged: { editing in
                    dragging = editing
                }.padding()
                .tint(.blue)

            }

        }
    }
}
```

