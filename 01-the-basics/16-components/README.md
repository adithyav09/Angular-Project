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
    selector: 'app-server'
    templateUrl: './server.component.html'
})
export class SeverComponent {

}
```