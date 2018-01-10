# Junior Golf Hub
  
## Angular-Tests

### TEST 1:

##### Description:  Following files are 2 component files for an election campaign project. Child component needs to be implemented in the parent component such that all people in the array list taken from people.ts are displayed one-by-one.





```typescript
•	app/person-child.component.ts


import { Component, Input } from '@angular/core';

import { Person } from './person;

@Component({
  selector: 'app-person-child',
  template: `
    <h3>{{person.name}} says:</h3>
    <p>I, {{person.name}}, am running for election against, {{rivalName}}.</p>
  `
})
export class PersonChildComponent {
  @Input() person: Person;
  @Input('rival') rivalName: string;
}

```




```typescript

•	app/person-parent.component.ts


import { Component } from '@angular/core';
 
import { PEOPLE } from './person;
 
@Component({
selector: 'app-person-parent',
template: `
<h2>{{rival}} is against {{people.length}} people</h2>
<app-person-child  <<DIRECTIVE>> ="<<ARRAY OPERATION>>"
[person]="person"
[rival]="rival">
</app-person-child>
`
})
export class HeroParentComponent {
people = PEOPLE;
rival = 'John';
}

•	app/person.ts

export class Person {
  name: string;
}

export const PEOPLE  = [
  {name: 'Jackie'},
  {name: 'David'},
  {name: 'Arnold'}
];
```


### TEST 2:

##### Description: This code needs necessary imports, decorators and definitions, to pass string from app.firstsvc to app.component, using function getFirstSvc() defined in app.firstsvc.

```typescript
•	/app/app.firstsvc.ts.
import { *INSERT NECESSARY IMPORT* } from '@angular/core'; 

*INSERT NECESSARY DECORATOR* 
export class firstSvc {  
   getFirstSvc(): string { 
      return "Good Day!"; 
   } 
}
```

```typescript

•	/app/app.component.ts


import { Component } from '@angular/core';  

import { firstSvc } from './app. firstsvc;  

@Component({ 
   selector: 'my-app', 
   template: '<div>{{value}}</div>', 
   providers: [firstSvc]  
}) 

export class AppComponent { 
   value: string = ""; 
   constructor(*INSERT NECESSARY DEFINITION *) { } 
   ngOnInit(): void { 
      this.value = this._firstSvc.getFirstSvc(); 
   }   
}
```

### TEST 3:

##### Description: These files show implement URL building, HTTP handling, under Aspect-Oriented Programing protocols. Invoice.service.ts needs the necessary decorators and imports, if it needs to make itself available to aspect. Define a function to establish mapping of JSON response.




```typescript
•	alllogs.aspect.ts

import {Injectable} from '@angular/core';
import {beforeMethod, Metadata} from 'aspect.js/dist/lib/aspect';
@Injectable()
export class LoggingAspect {
    
  @beforeMethod({
    classNamePattern: /(Invoice|Customer)Service/,
    methodNamePattern: /^(get)/
  })
  invokeBeforeMethod(meta: Metadata) {
    console.log(`Inside of the logger.
      Called ${meta.className}.${meta.method.name}
      with args: ${meta.method.args.join(', ')}.`
    );
  }
}
```







```typescript
•	invoice.service.ts

import {Injectable} from '@angular/core';
import {Http} from '@angular/http';
import {Observable} from 'rxjs/Observable';
import 'rxjs/Rx';
*NECESSARY IMPORTS FOR DECORATOR *
import {Invoice} from './invoice.model';
@Injectable()
*INSERT NECESSARY DECORATOR*
export class InvoiceService{
  private url: string;
  constructor(private http: Http) {
    this.url = '/data/invoices/data.json';
  }
  get(): Observable<Invoice[]> {
    return this.http.get(this.url).*INSERT NECESSARY MAP FUNCTION*
}
}
```
