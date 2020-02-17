# Animations



### Simple animation

```swift
struct PetView: View {
  var pet: Pet
  @State private var zoomed = false

  var body: some View {
    Image(pet.imageName)
      .resizable()
      .aspectRatio(contentMode: zoomed ? .fill : .fit)
      .tapAction { 
        withAnimation { self.zoomed.toggle() }
      }
  }
}
```

The transitions for animations must be added to the elements being animated. Here is an example for an image that's being 

```swift
var body: some View {
  @State private var showClaws = false

  HStack {
    Image("show")
      .tapAction {
        withAnimation(.basic(duration: 2)) {
          self.showClaws.toggle()
        }
      }

    if showClaws {
      Image("claws")
        .font(.title)
        .padding(.all)
        .transition(.move(edge: .leading))
    }
  }
}

```

