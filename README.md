# TabView-vertical-sliding
Vertical sliding through TabView
# The first part
![IMG_0140](https://github.com/S-way520/TabView-vertical-sliding/assets/95877651/48cd4acc-d259-4368-833c-39dcda717b22)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
private let Count = ["o", "o", "o", "o", "o"]
struct ContentView: View {
    @State private var selected = 0
    var body: some View {
        ZStack {
            Selected
            HStack {
                VStack{
                    ZStack{
                        VStack {
                            Capsule()
                                .fill(Color.blue)
                                .frame(width: 10, height: 10)
                                .offset(y: CGFloat(selected * 38))
                                .animation(.default, value: selected)
                        }
                        .frame(height: 160, alignment: .top)
                        .padding(5)
                        .background(Color.red)
                        .cornerRadius(10, antialiased: true)
                        .padding(.horizontal, 30)
                        VStack {
                            ForEach(0..<Count.count, id: \.self){ index in
                                Text(Count[index])
                                    .fontWeight(self.selected == index ? .bold : nil)
                                    .font(.subheadline)
                                    .foregroundColor(self.selected == index ? .blue : .black)
                                    .frame(width: 50, height: 30)
                                    .onTapGesture {
                                        self.selected = index
                                    }
                            }
                        }
                        
                    }
                }
                Spacer()
            }
        }
    }
}
extension ContentView {
    private var Selected : some View {
        TabView(selection: $selected) {
            OneView().tag(0).rotationEffect(Angle(degrees: -90), anchor: .center)
            Text("2").tag(1).rotationEffect(Angle(degrees: -90), anchor: .center)
            Text("3").tag(2).rotationEffect(Angle(degrees: -90), anchor: .center)
            Text("4").tag(3).rotationEffect(Angle(degrees: -90), anchor: .center)
            Text("5").tag(4).rotationEffect(Angle(degrees: -90), anchor: .center)
        }
        .frame(width: 250, height: 400)
        .background(Color.gray)
        .tabViewStyle(.page(indexDisplayMode: .never))
        .padding(.bottom, 30)
        .rotationEffect(Angle(degrees: 90), anchor: .center)
    }
}
```
Code file 3
```swift
import SwiftUI
struct OneView: View {
    var body: some View {
        Text("1234567890122987654189397541417829200272635353683939")
    }
}
```
