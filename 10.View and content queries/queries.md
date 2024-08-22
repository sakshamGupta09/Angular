# Queries

## Why

- To access reference of child components, directives, DOM elements present in my template.
- There are two types of queries

## View queries

- View refers to the elements defined in the component's own template.
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
