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
- This happens if the target is hidden by `@If` or not present in the view at all.

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

## Query Locators

- We now know how to query for a component or a directive.
- But what about DOM elements.
- This first parameter for each query decorator is its locator.
- We can specify a string which matches witrh a template reference variable.
- `@ViewChild('save') saveButton: ElementRef<HTMLButtonElement>;`

## Query options

- Query decorator accepts a second argument which is an object.

## Static queries

- `@ViewChild` and `@ContentChild` queries accept the static option. Not for children.
- `@ViewChild(CustomCardHeader, {static: true}) header: CustomCardHeader;`.
- If the target element is always present and not conditionally rendered.
- We do not need to wait till `afterViewInit` hook and can access it inside `OnInit` hook.

## Contend descendants

- By default, content queries find only direct children of the component and do not traverse into descendants.
- [Example](https://angular.dev/guide/components/queries).
- By setting `descendants: true`, you configure the query to traverse all descendants in the same template.
- View queries do not have this option because they traverse descendants by default.

## Common query pitfalls

- Do not directly write state to child components.
- 

