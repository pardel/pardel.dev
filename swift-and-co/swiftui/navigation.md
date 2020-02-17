# Navigation

Includes the Navigation View and its stack.

```swift
var body: some View {
  NavigationView {
    someView {

    }
      .navigationBarItems(trailing: EditButton())
      .navigationBarTitle(Text("Sleeps"))
  }
  }
```

### Navigation button

Allows for navigation to happen, views that act as links must be wrapped in a `NavigationButton` view:

```swift
var body: some View {
  NavigationView {
    List(pets) { pet in
      NavigationButton(destination: PetDetails(pet.name)) {
        PetCell(pet: pet)
      }
    }
  }
  }
```

The destination parameter must be a view - event a simple `Text` view will do.

It also automatically adds the disclosure indicator.

### Navigation Bar Title

Defined as modifier for the `View` that is shown on the screen \(similar to self.title in `UIView`s\):

```swift
struct PetView: View {
  var pet: Pet

  var body: some View {
    Image(pet.imageName)
      .resizable()
      .navigationBarTitle(Text(pet.name), displayMode: .inline)
  }
}
```

### Navigation Bar Buttons

```swift
struct PetsView: View {
  var pets: [Pet]

  var body: some View {
    List {
      ForEach(store.pets) { pet in
        PetCell(pet: pet)
      }
    }
      .navigationBarTitle(Text("Pets), displayMode: .inline)
      .navigationBarItems(trailing: EditButton())
  }
}
```

### iPad Specifics

As the detail view is always displayed in portrait mode, we should indicate that the NavigationView has both pieces of content \(left navigation + right detail\):

```swift
var body: some View {
  NavigationView {
    PetsList()
    PetDetailsPlaceholder()
  }
```

