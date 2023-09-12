# Data binding and String interpolation

Databinding = Communication

TypeScript code -> TemplateHTML

Output Data (->):
- string interpolation
- property binding


## String interpolation
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

## Property Binding
```html
<button class="btn btn-primary"
disabled>Add Server</button>
<app-server></app-server>
<app-server></app-server>
```

```typescript
@Component({
  templateUrl: './servers.component.html',
})
```


React to (user) Events (<-):
- event binding

combination of both(<->):
- Two-Way-Binding 

