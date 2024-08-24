# Styling components

## Style scoping

## Why do we need style scoping

- If styles are not scoped, every style we introduce becomes global.
- Everytime a new style is intoduced, there is a risk that we migt override an existing style.
- **Style conflicts** Everytime a new style is introduced, we have to check if that style elready exists.
- That makes our codebase hard to maintain.
- **Maintaining Component Encapsulation** We can be certain that styles introduced in a component won't affect other 
  components.


## How Angular achieves scoping

- Every component has a property called `encapsulation` in the decorators' metadata.
- It can take three values `None`, `Emulated`, `ShadowDom`
