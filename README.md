# AngularZeroToMastery

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 14.0.5.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

## Angular AOT and JIT

<img src="src\Images\Angular-Aheadoftimecompilation.png" alt="AOT" width="700" height="300" title="AOT">
<img src="src\Images\Angular-JIT Compilation.png" alt="JIT" width="700" height="300" title="JIT">
<img src="src\Images\Compilerplatformpointcode.png" alt="Compiler" width="700" height="300" title="compiler">
<img src="src\Images\JITvsAOT.png" alt="AOTvsJIT" width="700" height="300" title="AOTvsJIT">

## Change detection
Change detection is a process to update the html of an app once anything changes in the backend

change detection occurs
1. When the app is initialized
2. During change in our data
3. Manually triggering change detection

Change detection runs twice when app is initialized
To stop this we can add `import { enableProdMode } from '@angular/core';` in `main.ts` file
This will disabe the change detection running two times at the time of initialization

## Javascript Expressions
A javascript is a single line of code that can be evaluated to a single output value. The value can be a number, a string or a logical value.

Expressions in angular is displayed using curly brackets {{}}
This is also called string interpolation.

Expression is the code that is inside the curly brackets
string interpolation is the process of replacing placeholders into string values

The expression `{{name}}` is interpolated into John

expressions can also contain method calls.
`{{name.toUpperCase}}, {{getName()}} <p>{{15+13}</p>`

## Property Binding
[attribute]

in component ts - `imgURL = "https://url"` then in template `<img [src] = imgURL/>`

We can apply property binding to any attribute in out documents
If angular comes across an attribute with square brackets, it'll process the attribute before rendering.

## Event Binding
`<input (keyup) = "changeImage($event)" [value]="imgURL">`

the event is passed to the component to pass data to the method

//as is using type assertion feature of typescript

`changeImage(e: KeyboardEvent)
{
    this.imgURL = (e.target as HTMLInputElement).value
}`

## Components
creating a component -> `ng generate component`

adding decorator at class level -> `import {Input} from '@angular/core';`

adding decorator at property level -> `@Input() postImg = ''`

angular supports property binding on components

using alias at decorator level `@Input('img') postImg = ''`

In the parent component -> `<child-com [img] = "imgURL"></child-com>`

## Emitting Events

we can send data from child component to parent component using the event emitter

we will use the @Output decorator for the params we want to send to the parent

we will add or import the decorator in the component `import {Component, Input, EventEmitter} from @angular/core`

in component class - creating an event
`@Output() imgSelected = new EventEmitter<string>()`

in template - emitting an event
`<img [src]="postImg" (click)="imgSelected.emit(postImg)>`

listen to event in parent component
`<app-post [img] = "imgURL" (imgSelected)="logImg($event)"></app-post>`

logImg method will be in the parent component class

## Content Projection - Passing data from parent to child component
Content projection is the process of loading content inserted into a component tag.

Angular creates a custom element for handling most of the work which is <ng-content></ng-content> element

## LifeCycle Functions
Angular gives us the option of having refined control over the changes in our components through lifecycle hooks. 
They are functions that run during events and our components. Specifically they run when components are experiencing changes

first id constructor() which is used when we initialize a component
second is ngonInit(). component implmenents an interface OnInit

ngOnInit() - A callback method that is invoked immediately after the default change detector had checked the directive's data-bound properties for the first time,
and before any of the view or content children has been checked. It is invoked only once when the directive is instantiated.

ngOnChanges hook implements OnChanges interface - will run whenever changes are made to the component - run atleast once
ngDoCheck hook implements DoCheck interface  - after a change detection cycle has occured - run atleast twice

Two life cycle hooks for content and two for the view

ngAfterContentInit - implements interface AfterContentInit
ngAfterContentChecked - implements interface AfterContentChecked
ngAfterViewInit - implements interface AfterViewInit
ngAfterViewChecked - implements interface AfterViewChecked

## View Vs Content
<img src="src\Images\ViewVsContent.png" alt="AOT" width="700" height="300" title="AOT">

## Pipes
A pipe is a function for transforming a value in the template. Pipes are not specific to a componenet like a function, we can use it everywhere. Pipes are available in the browser module.

The purpose of the pipe is to transform the value for the templates. The original value will remain the same in the class.

we can use prebuilt pipes or create our own pipes. Json pipe is a pipe used only for debugging and showing json data in template.

## Directives
Attribute Directives - changes the appearance or the behaviour of an element
Structural Directives - Add or remove elements from the DOM

ngClass directive - its an attribute directive that allow is to change the classes of an element based on conditions dynamically.

`<button (click) = "blueClass = !blueClass" [ngClass]="{blue:blueClass}">Change</button>`

ngStyle directive - 
