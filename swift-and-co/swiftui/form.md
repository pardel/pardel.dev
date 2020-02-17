# Form

Similar to `VStack`, it is a container built specific to provide controls in a form - makes forms on multi-platform really easy.

```swift
Form {
  Section(header: Text("General characteristics").font(.title)) {
    Toggle(isOn: $pet.bites) { ... }
    Stepper(value: $pet.claws, in: 0...10) { ... }
  }
  Section {
    Button(action: submitUpdate) { Text("Update") }
  }
}
```

### Button

Can be customised to include combination of views - eg: vertical image and text:

```swift
Button(action: submitUpdate) {
  VStack {
    Image("save")
    Text("Update")
  }
```

### Toggle

```swift
Toggle(isOn: $pet.bites) {
  Text("Does bite")
}
```

One can provide a label as image with text:

```swift
Toggle(isOn: $pet.bites) {
  Image("bite", label: Text("Does bite"))
}
```

or event a custom shape:

```swift
Toggle(isOn: $pet.bites) {
  CustomShape().accessibility(label: Text("Does bite"))
}
```

### Picker

Selecting one values from a lot of options. Has 3 core properties: `options`, `selection`, `label`.

```swift
Picker(selection: $pet.color, label: Text("Color:")) {
  Text("White).tag(Color.white)
  ...
}
```

#### Picker styles

`radioGroup` or \`\` \(default\).

```swift
Picker... {
}.pickerStyle(.radioGroup)
```

