# Gestures

### Tap

```swift
struct PetView: View {
  var pet: Pet

  var body: some View {
    Image(pet.imageName)
      .tapAction {
        ...
      }
  }
}
```

