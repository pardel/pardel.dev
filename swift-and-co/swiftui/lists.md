# Lists

```swift
List(0..<5) { item in
  Text("\(item)")
}
```

### `List` vs. `ForEach`

Both take a collection and a `View` builder to maps each data item into its own `View`:

```swift
List { pet in
  PetCell(pet: pet)
}
```

```swift
ForEach(pets.toys) { toy in
  ToyIcon(toy: toy)
}
```

The difference is: ForEach doesn't add any visual effects of its own - it simply adds its own contents to its container.

### Using Objects

Data displayed need to conform to `Identifiable` - have an `id` property of type `UUID`.

```swift
struct Pet : Identifiable {
  var id = UUID()
  var name: String
  var color: String
  var type: String
  var imageName: String { return name }
}
```

```swift
struct ContentView: View {
  var pets: [Pet] = []

  var body: some View {
    List {
      ForEach(store.pets) { pet in
        PetCell(pet: pet)
      }
    }
  }
}
```

### Action Buttons

```swift
List {
  Button(action: addPet) { 
    Text("Add Pet")
  }
  ForEach(store.pets) { pet in
    PetCell(pet: pet)
  }
}
```

### Sections

```swift
List {
  Section {
    Button(action: addPet) { 
      Text("Add Pet")
    }
  }
  Section {
    ForEach(store.pets) { pet in
      PetCell(pet: pet)
    }
  }
}
```

### List Style

```swift
List {
  ...
}
.listStyle(.grouped)
```

### Deletion & Moving

```swift
var body: some View {
  List {
    ...
    Section {
      ForEach(store.pets) { pet in
        PetCell(pet: pet)
      }
        .onDelete(perform: delete)
        .onMove(perform: move)
    }
  }
}

func delete(at offsets: IndexSet) {
  store.pets.delete(atOffsets: offsets)
}

func move(from source: IndexSet, to destination: Int) {
  store.pets.move(fromOffsets: source, toOffset: destination)
}
```

### Test Data

Test data can be defined beside the `struct` \(in the same file\) to drive Views and debugging the app:

```swift
#if DEBUG
let testData = [
  Pet(name: "Hedwig", type: "Snowy Owl", color: "white"),
  Pet(name: "Scabbers", type: "Rat", color: "brown"),
  Pet(name: "Crookshanks", type: "Half-cat, Half-Kneazle", color: "ginger")
]
#endif
```

To use this data in previews, simply pass it to your View in the `_Previews`:

```swift
struct ContentView: View {
  ...
}

#if DEBUG
struct ContentView_Previews : PreviewProvider {
    static var previews: some View {
        ContentView(pets: testData)
    }
}
#endif
```

