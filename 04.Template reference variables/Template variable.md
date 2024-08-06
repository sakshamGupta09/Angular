# Template variables

## Why

- Use data from one part of template in another part of template without involving class.

## Syntax

- Hash symbol and then the name of the variable.
- #variableName
- `<input #phone placeholder="phone number" />`.
- `<button type="button" (click)="callPhone(phone.value)">Call</button>`.

## What template variable refers to

- If you declare the variable on a component, the variable refers to the component instance.
- If you declare the variable on a standard HTML tag, the variable refers to the DOM node.
- If you declare the variable on an `<ng-template>` element, the variable refers to a `TemplateRef` instance which represents the template.
- In short it refers to the element on which the vraibale is declared.

## Variable specifying a name

- How can we access the directive using template variable ?
- If the variable specifies a name on the right-hand side, such as `#var="ngModel"`, the variable refers to the directive or component on the element with a matching exportAs name.

## Scoping

- If, for, switch and template creates there own scope.
- Template variables declared inside this scope are not accessible to the outside world.

## Template input variables

- The variables that we pass to `ng-template` using let keyword are called template input variables.
