
# Picker

Picker를 활용해서 값을 선택하는 다양한 UI를 구현합니다.

```swift
struct Picker_Tutorials: View {
    @State private var selected: Sports = .soccer
    
    var body: some View {
        List {
            HStack {
                Spacer()
                Text(selected.rawValue)
                    .font(.system(size: 200))
                Spacer()
            }
            
            Picker("Favorite", selection: $selected) {
                ForEach(Sports.allCases) { item in
                    Text(item.rawValue)
                }
            }
//            .pickerStyle(.inline)
//            .padding()
        }
//        VStack {
//            Text(selected.rawValue)
//                .font(.system(size: 200))
//            
//            Picker("Favorite", selection: $selected) {
////                Text("soccer").tag(Sports.soccer)
////                Text("basketball").tag(Sports.basketball)
////                Text("baseball").tag(Sports.baseball)
//                
//                ForEach(Sports.allCases) { item in
//                    Text(item.rawValue)
//                }
//            }.pickerStyle(.segmented)
//            .padding()
//        }
    }
}
```

## Summary
 - Q&A
    - Q. 동적으로 피커 뷰의 선택 란을 만드는 과정에서 "바인딩과 타입이 일치하기 때문에"가 무슨 의미인가요? 어떻게 별도 `.tag` modifier없이 연동할 수 있는지 궁금해요.
    - A. ForEach는 파라미터로 전달받은 모델이 `Identifiable`을 채용하고 있다면 id 속성으로 구분할 수 있습니다. 그래서 `tag` 없이도 각 항목을 구분할 수 있습니다. 모델이 Identifiable을 채용하고 있지 않다면 ForEach로 id 파라미터를 함께 전달해서 구분할 속성을 지정해 주면 됩니다. 강의에 나오는 설명은 `@State 바인딩`과 `ForEach가 열거하는 타입`이 일치한다는 의미인데 중요한 부분이 빠져서 의미 전달이 제대로 되지 않는것 같습니다. 향후 업데이트 시에 보강하도록 하겠습니다.
