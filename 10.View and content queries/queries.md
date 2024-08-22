# Queries

## Why

- To access reference of child components, directives, DOM elements present in my template.
- If we have a child component, directive some DOM node in our template, we can access it in the model file.
- There are two types of queries

## View queries

- View refers to the elements defined in the component's own template not projected from parent.
- View queries search elements in the component's view.
- Since we are querying the view, we should run our queries in `AfterViewInit`.
- View query results become available in the `ngAfterViewInit` lifecycle method. Before this the value is `undefined`.
- If the query does not find a result, its value is `undefined`.
- This happens if the target is hidden by `@If`.

## @ViewChild

- To get a single result from the query.
- First match is returned.
- `@ViewChild(CustomCardHeader) header: CustomCardHeader;`

## @ViewChildren

- To get multiple matching results.
- `@ViewChildren(CustomCardAction) actions: QueryList<CustomCardAction>;`
- We can iterate this list using `forEach`.

## Content queries

- Seraches in the content that has been projected by the parent.
- Results are available inside `afterContentInit` hook.

## @ContentChild

- To get a single result from the query.
- First match is returned.
- `@ContentChild(CustomCardHeader) header: CustomCardHeader;`

## @ContentChildren

- To get multiple matching results.
- `@ContentChildren(CustomCardAction) actions: QueryList<CustomCardAction>;`
- We can iterate this list using `forEach`.
