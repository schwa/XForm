# XForm

An alternative "Form" API for SwiftUI highlighting Swift's new 'ForEach(subviewsOf:)' and 'Group(subViewsOf:)' APIs

**further description forthcoming**

```swift
struct XForm <Content>: View where Content: View {
    let content: Content

    init(@ViewBuilder content: () -> Content) {
        self.content = content()
    }

    var body: some View {
        ScrollView(.vertical) {
            VStack {
                Group(subviewsOf: content) { subviews in
                    ForEach(subviews.dropLast()) { subview in
                        subview
                        Divider()
                    }
                    subviews.last
                }
            }
            .padding([.leading, .trailing])
        }
    }
}
```

## Screenshot

![alt text](<Documentation/Screenshot 2024-06-12 at 08.20.14.png>)
