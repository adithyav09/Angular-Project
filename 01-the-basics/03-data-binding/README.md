# Data binding and String interpolation

Databinding = Communication

TypeScript code -> TemplateHTML

## Output Data (->):
- string interpolation
- property binding


### String interpolation
in ```server.component.html``` add

```html
<p> {{ 'server' }} with ID {{ serverID }} is {{ getServerStatus }} </p>
```

where __'server'__ is a string (must be able to resolve to a string in databinding). __'serverID'__ also resolves to a string.

and add this to ```sever.componenet.ts```

```typescript
export class ServerComponent {
    serverID: number = 10;
    serverStatus: string = 'offline';
}

    getSeverStatus() {
        return this.getServerStatus;
    }
```

### Property Binding

In ```servers.component.html``` write where __disabled__ should be in square brackets:

```html
<button class="btn btn-primary"
[disabled]="!allowNewServer">Add Server</button>
<app-server></app-server>
<app-server></app-server>
```

Also add code below in the ```severs.component.ts``` to make button available after 2 seconds:

```typescript
@Component({
  templateUrl: './servers.component.html',
})

export class ServersComponent implements OnInit {
  allowNewServer = false;

  constructor() {
    setTimeout(() => {
      this.allowNewServer = true;
    }, 2000);
  }

  ngOnInit() {
  }
}
```
### Property Binding vs String interpolation

Can use property binding instead of string interpolation below in ```servers.component.ts```:

```typescript
<button
  class="btn btn-primary"
  [disabled]="!allowNewServer"
  (click)="onCreateServer()">Add Server</button>
<p [innerText]="allowNewServer"></p>
<p>{{ serverCreationStatus }}</p>
<app-server></app-server>
<app-server></app-server>
```

**Note**: Don't mix property binding and string interpolation.

If you want to output something in your template use string interpolation.

If you want to change some property (html element, directive, or component) use property binding.

## React to (user) Events (<-):
- event binding

Code below belongs in ```servers.component.ts```:

```html
<button
  class="btn btn-primary"
  [disabled]="!allowNewServer"
  (click)="onCreateServer()">Add Server</button>
<!--<p [innerText]="allowNewServer"></p>-->
<p>{{ serverCreationStatus }}</p>
<app-server></app-server>
<app-server></app-server>
```

In ```servers.component.ts```:

```typescript
export class ServersComponent implements OnInit {
  allowNewServer = false;
  serverCreationStatus = 'No server was created!';
  
    constructor() {
        setTimeout(() => {
        this.allowNewServer = true;
        }, 2000);
    }
    ngOnInit() {
    }

    onCreateServer() {
        this.serverCreationStatus = 'Server was created! Name is ' + this.serverName;
    }
}
```
#### Bindable Properties and Events
How do you know to which Properties or Events of HTML Elements you may bind? You can basically bind to all Properties and Events - a good idea is to ```console.log()```  the element you're interested in to see which properties and events it offers.

Important: For events, you don't bind to onclick but only to click (=> (click)).

The MDN (Mozilla Developer Network) offers nice lists of all properties and events of the element you're interested in. Googling for YOUR_ELEMENT properties  or YOUR_ELEMENT events  should yield nice results.


## combination of both(<->):
- Two-Way-Binding 

The ```($event)```

```html
<label>Server Name</label>
<input
  type="text"
  class="form-control"
  (input)="onUpdateServerName($event)">
<button
  class="btn btn-primary"
  [disabled]="!allowNewServer"
  (click)="onCreateServer()">Add Server</button>
<!--<p [innerText]="allowNewServer"></p>-->
<p>{{ serverCreationStatus }}</p>
<app-server></app-server>
<app-server></app-server>
```