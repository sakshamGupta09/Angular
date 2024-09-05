# Change detection

- Angular's job is to keep the model and view in sync.
- Whenever the model is updated, the view is synchronized as well.
- Change detection means checking if the model has updated and then update the view accordingly.

## When does our application state changes

- Typically async operations like `setTimeout`, `setInterval`, `httpRequests`, `DOM Events` can cause a state update.
- We need a mechanism which tells angular about the completion of async events.


## Zone js

- Zone js notifies angular when the async events has completed, so that angular can perform change detection.
- Zone js cannot tell angular what state in what component has changed. It just tells that some state in some component might have changed.
- That is why angular has to check for changes for the entire view tree.
- This is the problem that signals solve.

## Default change detection

