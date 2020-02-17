---
description: Managing State
---

# State

A `View` defines its dependencies. This can be done in 3 different ways:

### @State property

Storage is automatically allocated by SwiftUI on the `View`'s behalf and exists outside the app's storage.

```swift
struct PetView: View {
  var pet: Pet
  @State private var zoomed = false

  var body: some View {
    Image(pet.imageName)
      .resizable()
      .aspectRatio(contentMode: zoomed ? .fill : .fit)
      .tapAction { self.zoomed.toggle() }
  }
}
```

### @Binding Property Wrapper

Just like `@State` but without ownership. Provides read & write without ownership:

```swift
struct AttackButton: View {
  @Binding var isAttacking: Bool

  var body: some View {
    Button( action: {
      self.isAttacking.toggle()
    }) {
      Image(systemImage: isAttacking ? "pause.circle" : "play.circle")
    }
  }
}
```

The state of isAttacking is owned by the 'parent' view and provided when `AttackButton` is created:

```swift
struct PetView: View {
  let pet: Pet
  @State private var isAttacking: Bool = false

  var body: some View {
    VStack {
      ...
      AttackButton(isAttacking: $isAttacking)
    }
  }
}
```

### BindableObject

Protocol used for data when its source is not the current `View`.

```swift
class PetStore: BindableObject {
  var pets: [Pet] {
    didSet { didChange.send() }
  }

  init(pets: [Pet] = [] ) {
    self.pets = pets
  }

  var didChange = PassthroughSubject<Void, Never>()
}
```

`PassthroughSubject` - `didChange` is a local object we can send notifications to, similar to the `NotificationCenter`.

Now, our `View` will consume the store as a `@ObjectBinding` property:

```swift

struct ContentView: View {
  @ObjectBinding var store = PetStore()

  var body: some View {
    List {
      ForEach(store.pets) { pet in
        PetCell(pet: pet)
      }
    }
  }
}
```

