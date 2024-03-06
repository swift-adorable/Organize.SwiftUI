
# Font

Font를 다루는 다양한 방법에 대해 공부합니다.
- Standard Text Styles 
- Font Designs
- Size and Weight
- Font Styles

### Standard Text Styles

```swift
struct StandardTextStyle: View {
    var body: some View {
        Text("Large Title")
            .font(.largeTitle)
//              #Title
//            .font(.title)
//              #HeadLine
//            .font(.headline)
//              #SubHeadLine
//            .font(.subheadline)
//              #Body
//            .font(.body)
//              #CallOut
//            .font(.callout)
//              #Caption
//            .font(.caption)
//              #Footnote
//            .font(.footnote)
    }
}
```

### Font Designs

```swift
struct FontDesign: View {
    var body: some View {
        Text("Font Design")
            .font(.largeTitle)
//            #MonoSpcaed
//            .font(.system(.largeTitle, design: .monospaced))
//            #Rounded
//            .font(.system(.largeTitle, design: .rounded))
//            #Serif
//            .font(..system(.largeTitle, design: .serif))
    }
}
```

### Font Size and Weight

```swift
struct FontSizeAndWeight: View {
    var body: some View {
        Text("50pt Font")
            .font(.system(size: 30))
//            #Black
//            .font(.system(size: 30, weight: .black))
//            #Heavy
//            .font(.system(size: 30, weight: .heavy))
//            #Bold
//            .font(.system(size: 30, weight: .bold))
//            #Semibold
//            .font(.system(size: 30, weight: .semibold))
//            #Medium
//            .font(.system(size: 30, weight: .medium))
//            #Regular
//            .font(.system(size: 30, weight: .regular))
//            #Light
//            .font(.system(size: 30, weight: .light))
//            #Thin
//            .font(.system(size: 30, weight: .thin))
//            #Ultralight
//            .font(.system(size: 30, weight: .ultraLight))
    }
}
```

### Font Styles

```swift
struct FontStyle: View {
    var body: some View {
        VStack(spacing: 20) {
            Text("No Style")
                .font(.system(size: 40))
              
            Text("Bold")
                .font(.system(size: 40))
                .bold()
              
            Text("Italic")
                .font(.system(size: 40))
                .italic()
              
            Text("Underline")
                .font(.system(size: 40))
                .underline()
              
            Text("Strikethrough")
                .font(.system(size: 40))
                .strikethrough()
              
            Text("123")
                .font(.system(size: 40))
              
            Text("Monospaced 123")
                .font(Font.system(size: 40).monospacedDigit())
              
            HStack {
                Text("Small ")
                    .font(Font.system(size: 40))
                  
                Text("Capitals")
                    .font(Font.system(size: 40).smallCaps())
            }
              
            Text("Lower Small Caps")
                .font(Font.system(size: 40).lowercaseSmallCaps())
              
            Text("Upper Small Caps")
                .font(Font.system(size: 40).uppercaseSmallCaps())
        }
    }
}
```

## Summary
- SwiftUI의 Font 구조체는 Apple Platform을 모두 지원 하고, Runtime에 System 기본 폰트를 자동으로 선택해 사용한다. Standard Text Style을 지원한다.
- Text의 default text style은 `.body`이다.
- Font Weight는 `.font(.system(size: 30, weight: .black))`, `.fontWeight(.black)` 두 가지 방법으로 지정이 가능하다.
