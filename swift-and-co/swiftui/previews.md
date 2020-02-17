# Previews

```swift
struct PetsView : View {
  var body: some View {
    ...
  }
}

#if DEBUG
struct PetsView_Previews : PreviewProvider {
  static var previews: some View {
    Group {
      PetsView()
      PetsView().environment(\.sizeCategory, .extraSmall)
      PetsView().environment(\.sizeCategory, .accessibilityExtraExtraLarge)
      PetsView().environment(\.colorScheme, .light)
      PetsView().environment(\.colorScheme, .dark)
      PetsView().environment(\.layoutDirection, .rightToLeft)
      PetsView().environment(\.locale, Locale(identifier: "ar"))
    }
  }
}
#endif

```

