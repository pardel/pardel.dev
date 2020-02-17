# Basic elements

### Text

```swift
Text("Learn-Swift.dev")
  .font(.headline)
  .foregroundColor(.secondary)
```

### Images

#### From assets

```swift
Image("imageName")
```

#### System images \(new in iOS 13\)

```swift
Image(systemName: "photo")
```

#### Resizable Image

```swift
Image("imageName")
    .resizable()
    .aspectRatio(contentMode: .fit)
```

### Spacer

A `View` that automatically expands to take all available space - usually employed when one needs to align 2 elements, one to the left and one to the right:

```swift
HStack {
  Text(pet.name),
  Spacer()
  Text(pet.color)
}
```

### Divider

A `View` that creates a line divider between 2 views:

```text
HStack {
  Text(pet.name),
  Divider()
  Text(pet.color)
}
```

