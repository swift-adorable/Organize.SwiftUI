
# Menu

메뉴를 표시하는 방법에 대해 공부합니다.

- 메뉴와 서브 메뉴
- Primary Action

```swift
struct Menu_Tutorials: View {
    var body: some View {
        VStack {
            
            Menu("File Menu") {
                
                Button("Copy", action: { })
                
                Button(action: {
                    
                }) {
                    Label("Change Folder Name", systemImage: "pencil")
                }
                
                Button(role: .destructive) {
                    
                } label: {
                    Label("Delete", systemImage: "trash")
                }
                
                Menu {
                    Button {
                        
                    } label: {
                        Label("Email", systemImage: "envelope")
                    }
                    
                    Button {
                        
                    } label: {
                        Label("Air Play", systemImage: "airplayvideo")
                    }
                    
                } label: {
                    Label("Share", systemImage: "Link")
                }
                
            }.padding()
            
            Menu("File Menu") {
                
                Button("Copy", action: { })
                
                Button(action: {
                    
                }) {
                    Label("Change Folder Name", systemImage: "pencil")
                }
                
                Button(role: .destructive) {
                    
                } label: {
                    Label("Delete", systemImage: "trash")
                }
                
                Menu {
                    Button {
                        
                    } label: {
                        Label("Email", systemImage: "envelope")
                    }
                    
                    Button {
                        
                    } label: {
                        Label("Air Play", systemImage: "airplayvideo")
                    }
                    
                } label: {
                    Label("Share", systemImage: "Link")
                }
                
            } primaryAction: {
                //Menu의 Main 동작이 이 클로저가 되며, 위의 Menu 옵션 동작을 원하면 꾹 누르면 된다.
                print("Do Something...")
            }.padding()
            
        }
    }
}
```

