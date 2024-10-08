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
- It can take three values `None`, `Emulated`, `ShadowDom`.

## ViewEncapsulation.Emulated

- Default
- Component's styles only apply to elements defined in that component's template.
- This mode ensures that a component's styles do not leak out and affect other components.
- However, global styles defined outside of a component may still affect elements inside a component with emulated.
- Angular generates a unique id and adds it as a HTML attribute to each and every element in the template.
- `_ngcontent-ng-c1253002314`
-  Unique id is also inserted into the CSS selectors defined in your component's styles.
-  `.card[_ngcontent-ng-c1253002314]`
-  Since this id is unique, it will never reference any other element.

## ::ng-deep

- Styles declared with this pseudoclass becomes global.
- Angular team strongly discourages this.

## ViewEncapsulation.None

- This mode disables all style encapsulation for the component.
- Any styles associated with the component behave as global styles.


## ViewEncapsulation.ShadowDom

- The problem with `Emulated ` mode was that the outside styles could still affect a component.
- This mode strictly guarantees that only that component's styles apply to elements in the component's template.
- Global styles cannot affect elements in a shadow tree.
- Styles inside the shadow tree cannot affect elements outside of that shadow tree.
