# Component Lifecycle

- Angular renders the components and also updates them.
- Lifecycle represents angular's process (a sequence of steps) in doing so.

## Lifecycle hooks

- While angular is following a step by step process to render or update a component, it intimates us that this step is
  now done, if you want to perform some action you can do it now.

## 1. Constructor

- Runs when angular creates an instance of the component class.
- An instance is now available.

## 2. OnChanges

- Runs everytime component's inputs have changed including the first time.
- If component has no inputs, it won't execute.
- Comparison is done by `===`.
- Can be used to react to changes in the input properties.
- Can update the state in this hook.

## Inspecting changes

- Since there can be multiple inputs and this hook runs everytime any of the inputs have changed.
- How do we learn which input property has changed?
- OnChanges accepts `SimpleChanges` which is an object.
- This object is a record. Key is inoput property name and value is `SimpleChange`.
- `SimpleChange` contains information like `previousValue`, `currentValue` and `firstChange`. 
