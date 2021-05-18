# Homework 2

## high level proces of how angular bootstrap process work

1. first of all the index.html file executed and loaded into the browser and the app-root component is rendered into the browser the app-root is a component but we are loading only the name of the selector of the component
2. the JS bundle is loading becouse Angular is a single page application first it reads the angular.json file then learn about the project configuration then based on the config it build the entire appliccation underneath angular CLI use webpack to bundel the javascript module ,when angular appliation ins build using `ng build --prod` there are same file are genearted to the folder to 'dist /appname'
   3.the main entry point start executing :this file is a containor for all Angular application by default the exectuion is configured under the angular.json file it is main.js so every time the bootsrap proces is started from main of the config  
   4 finaly ones we create ower own component we can import it to the app.module and create the tage into the template of the module and declare the selectoer name into @NgModule of the App module then it will render .

## Expain all the meta-data passed to @NgModule factory decorator? Use the official Angular docs.

### Decorator that marks a class as an NgModule and supplies configuration metadata.

1. providers: The set of injectable objects that are available in the injector of this module.

```
providers?: Provider[]

Example
class Greeter {
   greet(name:string) {
     return 'Hello ' + name + '!';
   }
}

@NgModule({
  providers: [
    Greeter
  ]
})
class HelloWorld {
  greeter:Greeter;

  constructor(greeter:Greeter) {
    this.greeter = greeter;
  }
}

```

2. declarations::::The set of components, directives, and pipes (declarables) that belong to this module.
```
declarations?: Array<Type<any> | any[]>

@NgModule({
  declarations: [NgFor]
})
class CommonModule {
}
```
3. imports::The set of NgModules whose exported declarables are available to templates in this module.
```
imports?: Array<Type<any> | ModuleWithProviders<{}> | any[]>

@NgModule({
  imports: [CommonModule]
})
class MainModule {
}
```

4. exports:::The set of components, directives, and pipes declared in this NgModule that can be used in the template of any component that is part of an NgModule that imports this NgModule. Exported declarations are the module's public API.
```
exports?: Array<Type<any> | any[]>
@NgModule({
  exports: [NgFor]
})
class CommonModule {
}
```
5. entryComponents::The set of components to compile when this NgModule is defined, so that they can be dynamically loaded into the view.
6. bootstrap:::The set of components that are bootstrapped when this module is bootstrapped. The components listed here are automatically added to entryComponents
```
bootstrap?: Array<Type<any> | any[]>
```
7. schemas::The set of schemas that declare elements to be allowed in the NgModule. Elements and properties that are neither Angular components nor directives must be declared in a schema.
```
schemas?: Array<SchemaMetadata | any[]>
```
8. id::A name or path that uniquely identifies this NgModule in getModuleFactory. If left undefined, the NgModule is not registered with getModuleFactory.
```
id?: string
```
9. jit::When present, this module is ignored by the AOT compiler. It remains in distributed code, and the JIT compiler attempts to compile it at run time, in the browser. To ensure the correct behavior, the app must import @angular/compiler.
```
jit?: true
```

# Explain how the default Emulated style encapsulation of Angular works?
Emulated view encapsulation (the default) emulates the behavior of shadow DOM by preprocessing (and renaming) the CSS code to effectively scope the CSS to the component's view

# Do your research on custom Web Components? What are they? and explain how the shadow DOM is important for creating custom Web Components.

Web Components is a suite of different technologies allowing you to create reusable custom elements — with their functionality encapsulated away from the rest of your code — and utilize them in your web apps
