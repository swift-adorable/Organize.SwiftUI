
# Stepper

Stepper로 범위를 지정하고 숫자를 선택하는 방법을 공부합니다.

```swift
struct Stepper_Tutorials: View {
    @State private var quantity = 1
    
    var body: some View {
        VStack {
            Text("\(quantity)")
                .font(.system(size: 150))
            
            Stepper("Quantity", value: $quantity)
                .padding()
            
            Stepper("Quantity") {
                quantity += 1
                
                if quantity >= 5 {
                    quantity = 1
                }
                
            } onDecrement: {
                quantity -= 1
                
                if quantity <= 1 {
                    quantity = 5
                }
            }
            .padding()
            .labelsHidden()
            
        }
    }
}
```
