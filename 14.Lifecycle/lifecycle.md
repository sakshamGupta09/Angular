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

## 3. OnInit

- Runs after angular has initialized all component inputs. We can access input properties here.
- Runs only once. So, ideal for setting up subscriptions or doing one time activities like api calls.
- Can update state.

## 4. DoCheck

- Angular performs change detection to learn if our bindings have changed.
- Befor checking it intimates us that I am going to perform checking.
- This hook runs very frequently, everytime befor angular goes to check for changes. Avoid defining it.
- Can be used for manual change detection.

## 5. AfterContentInit

- A component can recieve content from parent. This hook runs once after the content is initialized.
- As per the initial state of the component, content is initialized.
- Use this to read the results of `content queries`.
- Do not mutate state.
- Content is initialized before view.
- Runs only once.

## 6. AfterContentChecked

- Runs everytime after its content have been checked for changes meaning bindings have updated.
- When the state updates, content updates as well. It runs after that.
- Used to access the updated state of `content queries`.
- Since `ContentInit` runs only once, if we have to read the latest content query result we can use this hook.
- Runs very frequently so should be avoided.


## 7. AfterViewInit

- This hook runs once after the view is fully initialized.
- Use this to read the results of `view queries`.
- Do not mutate state.

## 8. AfterViewChecked

- Runs everytime after its view have been checked for changes meaning bindings have updated.
- Used to access the updated state of `view queries`.
- Since `ViewInit` runs only once, if we have to read the latest view query result we can use this hook.
- Runs very frequently so should be avoided.

## 9. AfterRender

- At a time in a page, we might have multiple components. When angular has rendered all of them into the DOM it runs.
- These functions are different from the other lifecycle hooks described in this guide.
- The execution of render callbacks are not tied to any specific component instance, but instead an application-wide hook.
- `afterRender` and `afterNextRender` must be called in an injection context, typically a component's constructor.
- If we have to use DOM api's in angular, this is the ideal hook.

## 10. OnDestroy

- Destroy means that component gets hidden using `@If` or navigating to another page.
- Just before the component is destroyed. Do you have any last wish.
- Use this to cleanup subscriptions or store some information.

## DestroyRef

- All the cleanup code currently resides in `Ondestroy`.
- We want to keep the setup code and cleanup code closer or together.
- `constructor(private destroyRef: DestroyRef) {}`.
- `destroyRef.onDestroy(() => {})`
