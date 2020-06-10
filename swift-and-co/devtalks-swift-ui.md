---
description: Project plan for "The brave new world of SwiftUI"
---

# DevTalks Swift UI

Start with a new project named "DevTalks"; open **ContentView.swift** and "**Resume**" in preview if required.

## List

1. Add List:

```swift
List {
   Text("Hello, World!")
}
```

2. Add messages property before body:

```swift
let messages = ["Hello Cluj", "Hello Bucharest"]
```

3. List becomes 

```swift
List(messages) { message in
    Text(message)
```

4. explain error - List becomes

```swift
List(messages, id:\.self) { message in
```

## Navigation controller to preview

1. in the Previews, around ContentView, add:

```swift
NavigationView {
    ContentView()
}
```

2. Add title for screen - in the view, at the end of List, add:

```swift
List(...) {
    ...
}.navigationBarTitle("DevTalks")
```

3. make the text smaller

```swift
.navigationBarTitle("DevTalks", displayMode: .inline)
```

## Cell formatting

1. add background to Text

```swift
.background(RoundedRectangle(cornerRadius: 10).fill(Color.blue))
```

2. add padding - add AFTER the background

```swift
.padding()
```

3. move BEFORE the background and length for padding:

```swift
.padding(10)
```

4. add foregroundColor after background

```swift
.foregroundColor(Color.white)
```

## Message sender or status

1. show Message.swift in WIP - move next to ContentView
   1. Explain Identifiable
   2. explain properties - direction
2. replace messages with:

```swift
let messages = [
    Message(id: "1", sender: "Alice", content: "Hello Cluj", direction: .incoming, wasDelivered: true, wasRead: true),
    Message(id: "2", sender: "Bob", content: "Hello Bucharest", direction: .outgoing, wasDelivered: true, wasRead: false),
    Message(id: "3", sender: "Charlie", content: "Hello Romania", direction: .incoming, wasDelivered: true, wasRead: true)
]
```

3. List becomes much simpler:

```swift
List(messages) { message in
    Text(message.content)
```

4. Adding a Vertical Stack with sender at the top:

```swift
VStack {
    Text(message.sender)
    ...
}
```

5. Left alignment

```swift
VStack(alignment: .leading) {
```

6. Smaller font

```swift
Text(message.sender).font(Font.caption)
```

7. Add a bit padding at the left and bottom

```swift
Text(message.sender).font(Font.caption).padding(.leading, 10).padding(.bottom, 4)
```

8. Add message status

```swift
Text(message.status).font(Font.footnote).padding(.leading, 10).padding(.top, 2)
```

9. What about outgoing messages that should be displayed on the right

```swift
HStack { 
    ... 
}
```

10. And a spacer:

```swift
HStack { 
    Spacer()
    ... 
}
```



## Incoming and Outgoing Views

Show **IncomingMessageView.swift** and **OutgoingMessageView.swift**

Move them next to ContentView

1. Delete everything inside List and replace with

```swift
if message.direction == .incoming {
    IncomingMessageView(message: message)
} else {
    OutgoingMessageView(message: message)
}
```



## Remove separators

Replace list with `ForEach` and add `ScrollView`:

```swift
ScrollView {
    ForEach(messages) { message in
        if message.direction == .incoming {
            IncomingMessageView(message: message)
        } else {
            OutgoingMessageView(message: message)
        }
    }
}
.padding()
.navigationBarTitle("DevTalks", displayMode: .inline)
```

Add `padding()`

## Take data outside the view

Having data inside the View is not a good sign - usually it comes from an api or similar.

1. I've already included a json file here with some data - Show & Move conversations.json
   1. a conversation has a name and a list of messages
2. I've also created a Conversation struct  & Move

```swift
...
```

x.

```swift
...
```



x.

```swift
...
```

x.

```swift
...
```



