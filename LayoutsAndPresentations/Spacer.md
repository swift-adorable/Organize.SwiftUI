
# Spacer

Spacer를 사용해서 공백을 추가하는 방법에 대해 공부합니다.

```swift
struct  Spacer_Tutorials: View {

    var body: some View {

        VStack(spacing: 0) { // #6

            //뷰가 확장 되지 않기 위해 아래 스페이서처럼 하거나, 뷰 전체에 패딩 탑을 준다
            //Spacer().frame(height: 1)

            HStack {
                Image(systemName: "suit.heart.fill")
                    .resizable()
                    .frame(width: 70, height: 70)
                    .foregroundColor(.white)
                    
                // #3
                Spacer()
            }
            .padding()
            .background(Color.blue)

            // #1
            Spacer().frame(height: 50)
            //Spacer(minLength: 50) //고정 여백이 아닌 최소 여백
            //고정 여백을 사용하려면 이니셜라이저에서 혹은 스페이서의 프레임

            VStack {
                // #5
                //Spacer()
                
                Image(systemName: "suit.spade.fill")
                    .resizable()
                    .frame(width: 70, height: 70)
                    .foregroundColor(.white)

                // #4
                //Spacer()
            }
            .padding()
            .background(Color.red)

            // #2
            Spacer()

            Spacer()

        }.padding(.top, 1)
    }
}
```
