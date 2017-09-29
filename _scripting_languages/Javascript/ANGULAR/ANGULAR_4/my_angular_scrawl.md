# My Angular Scrawl


```
simple angular implementation!
https://github.com/mgechev/light-angularjs
```
```
github: seeschweiler/angular-redux
```

```
https://jsonplaceholder.typicode.com/

```

```html
<a routerLink="/posts" routerLinkActive="my-active-css-class">Posts</a>

<a [routerLink]="['/posts', post.id]">Posts</a>

<a [routerLink]="['/posts', post.id]"  [queryParams]="{page: 123}">Posts</a>

```

```
- custom form validators
```

```typescript
this.activatedRoute.paramMap // ActivatedRoute
.subscribe((params) => {
    console.log(params) // an object representing the URL
    console.log(+params.get('id')) // /users/123 -->  123 // the `+` is to cast string to integer!
})

this.activatedRoute.queryParamMap.subscribe()


// this.activatedRoute.snapshot.paramMap.get('id') // does not get new values???
// this.activatedRoute.snapshot.queryParamMap.get('page')  // does not get new values???
```

```typescript
"123" === 123 // false
+"123" === 123 // true

d = new Date() // Tue Sep 26 2017 15:35:19 GMT-0700 (US Mountain Standard Time)
+d             // 1506465319859
```

```
Angular - Promise vs Observable

A Promise handles a single event when an async operation completes or fails.

Note: There are Promise libraries out there that support cancellation, but ES6 Promise doesn't so far.

An Observable is like a Stream (in many languages) and allows to pass zero or more events where the callback is called for each event.

Often Observable is preferred over Promise because it provides the features of Promise and more. With Observable it doesn't matter if you want to handle 0, 1, or multiple events. You can utilize the same API in each case.

Observable also has the advantage over Promise to be cancelable

Observable provides operators like map, forEach, reduce, ... similar to an array
```


```typescript
//combine observables:

import { Observable } from 'rxjs/Observable'
import 'rxjs/add/observable/combineLatest'
import 'rxjs/add/operator/map'
import 'rxjs/add/operator/switchMap'


let obs = Observable.combineLatest([
    this.activatedRoute.paramMap,
    this.activatedRoute.queryParamMap
])

obs.switchMap((combined) => { // not .map, because it does not return what we need
    let paramMap = combined[0]
    let queryParamMap = combined[1]

    let id = paramMap.get('id')
    let page = queryParamMap.get('page')

    return this.myService.getUser()
})
.subscribe((user) => {
    
})
```

```typescript
this.router.navigate(['/'])

// url with query params:
this.router.navigate(['/users', 123], {
    queryParams: {
        page: 123, foo: 'bar'
    }
}) // Router

```
```
 POST /api/authenticate - return a JWT

save JWT on localStorage

- send the JWT on the headders of our other http requests

- HTTP status code:  http://www.restapitutorial.com/httpstatuscodes.html

this.http.post('/api/auth', JSON.stringify(credentials))


<p (click)="authService.logout()">logout</p> // to log out, delete the token from localStorage

- check if the token has expired in the client, if so, destroy the token!

$ npm i angular2-jwt
import {JwtHelper} from 'angular2-jwt'


- for role based views, you can check if the current user has that role
```

```typescript
let myString:string = "aaa"
myString.endsWith(" world")
```

```html
<form #f="ngForm" (ngSubmit)="foo(f.value)">
    <input type="text" name="email" ngModel>
    <input type="password" name="password" ngModel>
</form>
```

```typescript
import {Http, RequestOptions, Headers } from '@angular/http'

let headers = new Headers()
headers.append('Authorization', 'Bearer sdjfhksdfhksjdf')

let options = RequestOptions({headers: headers})

this.http.get('/api/foo', options)
```

```bash
# custom angular directive

$ ng g d foo-bar

```




```typescript
type Role = 'guest' | 'basic' | 'admin'  // union
let role:Role = 'guest'
```

```html
<p *ngIf="foo.bar | async as x">{{x}}</p>
```

```bash
npm i stripe # payments
```


```html
<input type="text" [(ngModel)]="myControllerVar">

<input type="text" ngModel name="myControllerVar">

<input type="text" ngModel name="firstName" #firstName="ngModel" >
```



```html
<div ngModelGroup="contact" #contact="ngModelGroup">
<div *ngIf="!contact.valid">...</div>
    ...
</div>


ngModel creates a FormControl object under the hood!
ngForm -> creates a FormGroup under the hood, and uses (ngSubmit)
```

```html
<p>{{ foobar | json }}</p>
```

```html
//ngValue if you need to use complex objects
// but we will not use it in this situation
<option *ngFor="let x os xs" [ngValue]="x.id">{{x.name}}</option>

// so use this:
<option *ngFor="let x os xs" [value]="x.id">{{x.name}}</option>
```

```
sublime snippets:  tools > Developer > new snippet

source.js
text.html
save as: fooBar.sublime-snippet
$1 $2

to find the files:  sublime text > preferences > browse packages... > User
// /Users/brianspinos777/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/brianBootstrapRow.sublime-snippet 

```

```html
<form [formGroup]="myForm">
```

```typescript
import { Component, Pipe, PipeTransform} from '@angular/core'
import { Http, RequestOptions, Headers } from '@angular/http'
import { FormGroup, FormControl, Validators } from '@angular/forms'
import { Router } from '@angular/router';
```


```typescript
// properties in typescript:
// - like fields from the outside, but methods inside
// Foo.name 

get name(){
    return 'brian'
}

set name(n){
    this.name = n
}
```


```bash
$ ng g p pipes/my-summary/my-summary 
```



```html
{{ foo | mySummary:10 }}
```


```typescript
let actalLimit = (args) ? args : 50

if(!value)
    return null

return value.substr(0, actalLimit) + '...'
```

```html
<div *ngIf="username.pending">Loading...</div> // for async validator stuff
```