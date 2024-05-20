
# Link

외부 링크를 처리하는 특별한 뷰에 대해 공부합니다.

```swift
struct Link_Tutorials: View {
    let url = URL(string: "http://developer.apple.com")!
    let sms = URL(string: "sms://010-0000-0000")!
    
    var body: some View {
        VStack {
            Button("Apple Developer") {
            UIApplication.shared.open(url, options: [:], completionHandler: **nil**)
            }.padding()
            
            Link(destination: url) {
                Label("Apple Developer", systemImage: "house")
            }
            .padding()
            .background(.ultraThinMaterial, in: RoundedRectangle(cornerRadius: 12))
            // #2. Action Customizing
            .environment(\.openURL, OpenURLAction { url in
                if url.absoluteString.contains("kxcoding.com") {
                    print("Play \(url)")
                    return .handled
                    
                } else if url.absoluteString.hasPrefix("http://") {
                    var components = URLComponents(url: url, resolvingAgainstBaseURL: false)!
                    components.scheme = "https"
                    return .systemAction(components.url!)
                    
                } else if url.absoluteString.contains("badsite.com") {
                    return .discarded
                }
                
                return .systemAction
            })
            
            Link("Message", destination: sms)
        }
    }
}
```

## Summary
- Link는 iOS가 지원하는 url scheme을 모두 지원하고, universal link도 지원한다.
- Link Action을 Customizing 할 수 있다. (주석 #2. Action Customizing 참고)
