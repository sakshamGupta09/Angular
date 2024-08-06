# Template variables

## Why

- Use data from one part of template in another part of template without involving class.

## Syntax

- Hash symbol and then the name of the variable.
- `<input #phone placeholder="phone number" />`.
- `<button type="button" (click)="callPhone(phone.value)">Call</button>`.

## What template variable refers to

- If you declare the variable on a component, the variable refers to the component instance.
- If you declare the variable on a standard HTML tag, the variable refers to the DOM node.
- If you declare the variable on an <ng-template> element, the variable refers to a TemplateRef instance which represents the template.
