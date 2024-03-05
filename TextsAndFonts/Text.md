
# Text

문자열을 표시하는 가장 기본적인 뷰인 Text에 대해 공부합니다.

```swift
let longText = "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
  
struct  Text_Tutorials: View { 
    var body: some View {
        VStack {

            //  Text("Hello")
            //  .font(.largeTitle)
            //  .foregroundColor(.blue)
            //  .background(.gray)
              
            //  Text(verbatim: "Hello")
            
            Text(longText)
                .frame(width: 200) // 프레임 설정
                .lineLimit(10) // 줄 수 제한
                .truncationMode(.tail) // 생략 설정?
                .multilineTextAlignment(.center) //컨텐츠 정렬
                .lineSpacing(7) // 라인 여백
        }
    }
}
```

## Text
- Text Localization
    - 만약 Localization String을 사용한다면 `init<S>(S)`을 사용하고,
    - Locale에 영향을 받지 않으려면 `init(verbatim content: String)` 를 사용한다.
- 자주 사용되는 `modifier`
    - `font`: title, headline, body, footnote, caption 등 글꼴을 지정
    - `frame`: 텍스트의 Frame을 설정
    - `lineLimit`: 텍스트의 최대 줄 수를 제한
    - `lineSpacing`: 텍스트 줄 사이의 간격을 조정합니다.
    - `truncationMode`: 텍스트가 컨테이너를 넘어갈 때의 표시 방식을 설정
    - `multilineTextAlignment`: 여러 줄 텍스트의 정렬을 지정
