
# Label

문자열을 표시하는 가장 기본적인 뷰인 Text에 대해 공부합니다.

```swift
struct Label_Tutorials: View {
    var body: some View {
        VStack(spacing: 30) {
            //#1
            HStack {
                Image(systemName: "person")
                Text("User Profile")
            }
            .font(.largeTitle)
            
            //#2
            Label("User Profile", systemImage: "person")
                .font(.largeTitle)
            //#3
            HStack {
                Image("logo")
                    .resizable()
                    .aspectRatio(1.0, contentMode: .fit)
                    .frame(width: 60)
                    .clipShape(Circle())
                    .overlay {
                        Circle()
                            .stroke(lineWidth: 2)
                            .foregroundColor(.blue)
                    }
                Text("KxCoding")
                    .font(.largeTitle)
            }
            //#4
            Label {
                Text("KxCoding")
                    .font(.largeTitle)
            } icon: {
                Image("logo")
                    .resizable()
                    .aspectRatio(1.0, contentMode: .fit)
                    .frame(width: 60)
                    .clipShape(Circle())
                    .overlay {
                        Circle()
                            .stroke(lineWidth: 2)
                            .foregroundColor(.blue)
                    }
            }
        }
        .toolbar {
            Button {
            
            } label: {

                Label("User Profile", systemImage: "person")
                    .labelStyle(.titleAndIcon)
                //Label은 context에 따라 자동으로 표시 방식이 달라짐.
                //  HStack {
                    //  Image(systemName: "person")
                    //  Text("User Profile")
                //  }
            }    
        }    
    }
}
```

## Label
- #1과 #2, #3과 #4 는 각각 같은 View를 그린다.
- Label은 보통 Context에 따라서 자동으로 표시 방식이 달라진다.
- `.toolbar` modifier에서 Navigation Bar에서 사용 될 때는 **default** 로 이미지만 우선 노출된다.
    - `.labelStyle` modifier를 통해서 노출 우선 순위를 변경 할 수 있다.
