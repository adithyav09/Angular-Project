# Components

Keep in mind: Angular in the end is a JS framework, changing your DOM (HTML) at runtime!

## Creating a new component
- create a new folder (server) under app
- Within ```Server``` create a ```server.component.ts``` file.

- Name the file after ```ComponentNameComponent```
- Add a class decorator
- selctor should be used with the prefix ```app-```
- create a ```server.compoment.html```
- point the ```./server.component.html``` by assigning it to ```templateURL``` in ```server.component.ts```

```typescript
import { Component } from '@angular/core';

@Component({
    selector: 'app-server';
    templateUrl: './server.component.html'
})
export class SeverComponent {

}
```

## Role of App Module and Component Declaration

Angular uses modules to bundle components into packages

- Add ```ServerCompoment``` to the ```declarations``` under ```NgModule```

- Also need to import the ```ServerComponent``` without the extension added (webpack automatically installs extension):

```typescript
import {ServerComponent} from './server/server.component';
```

## Using Custom Components
- In ```app.component.html``` add:
```html
<h3>I'm in the AppComponent!</h3>
<hr>
<app-servers></app-servers>
```

## Creating Components with CLI & Nesting Components

```ng generate component servers``` or ```ng g c servers```creates a new component called __servers__ automatically

- four new files will generate one ```html, css, ts, spec.ts```

This goes in the ```servers.component.html```:

```html
<app-server></app-server>
<app-server></app-server>
```

In ```app.module.ts``` import and declare ```ServersComponent```:

```typescript
import { ServersComponent } from './servers/servers.component';

@NgModule({
  declarations: [
    AppComponent,
    ServerComponent,
    ServersComponent
  ],
  imports: [
    BrowserModule,
    FormsModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
```

Change ```app.component.html``` to use

```html
<app-servers></app-servers>
```

instead of
```html
<app-server></app-server>
```

which will populate the __servers__ component instead of __server__

## Working with Component Templates

change ```templateURL``` to ```template``` in ```servers.component.ts``` and use __backticks__ to define multi-line template:

```typescript
@Component({
  // selector: '[app-servers]',
  // selector: '.app-servers',
  selector: 'app-servers',
  template: `
    <app-server></app-server>
    <app-server></app-server>`,
  styleUrls: ['./servers.component.css']
})
```