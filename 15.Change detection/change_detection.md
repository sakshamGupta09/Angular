# Change detection

- Angular's job is to keep the model and view in sync.
- Whenever the model is updated, the view is synchronized as well.
- Change detection means checking if the model has updated and then update the bindings in the view accordingly.

## When does our application state changes

- We know view updates, when model does. So when does our model change?
- Typically async operations like `setTimeout`, `setInterval`, `httpRequests`, `DOM Events` can cause a state update.
- We need a mechanism which tells angular about the completion of async events.


## Zone js

- Zone js notifies angular when the async events has completed, so that angular can perform change detection.
- Zone js cannot tell angular what state in what component has changed. It just tells that some state in some component might have changed.
- That is why angular has to check for changes for the entire view tree.
- This is the problem that signals solve.

## Default change detection

- Whenever zone tells angular about completion of async event, angular checks the entire component tree for changes.
- This is bad because it is checking components which have nothing to do with the event.

## On Push

- Components with `OnPush` tells angular that please do not check my view bindings and that of my children's until I explicitly tell you to.
- I will decide if my state has changed and will raise a flag so that you can come and check my bindings.
- Angular will still traverse every component from top to bottom to check for changes, but those who are using `OnPush` but are not dirty will not be checked neither will be their children.
- Now the question is how do we show a flag to angular so that it can check our view bindings.

## MarkForCheck vs detectChanges

- `detectChanges` triggers change detection for the component and it's children.
- `markForCheck` just marks a component dirty and does not trigger a change detection. Because when async operation completes, zone will again ask angular to perform change detection.
- So with `OnPush` we should always use `markForCheck` otherwise with `detectChanges` we would be performing change detection two times.
- With `markForCheck` we end up with just one change detection cycle.
- All the ancestors of the component are also marked as dirty. Because when angular reaches to parent from top to bottom and if parent isn't marked dirty, it will not check child's bindings as well.

## Should we always call markForCheck when model changes

- By default for event handlers, angular marks the view dirty. So if we are updating data model within event handler we do not need to call `markForCheck`.
- When the `Input` property of a component changes, it is marked dirty by default. Values are compared by reference(===). This happens when angular checks bindings of parent.
- Async pipes

