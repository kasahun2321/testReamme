# Homework 2

## high level proces of how angular bootstrap process work

1. first of all the index.html file executed and loaded into the browser and the app-root component is rendered into the browser the app-root is a component but we are loading only the name of the selector of the component
2. the JS bundle is loading becouse Angular is a single page application first it reads the angular.json file then learn about the project configuration then based on the config it build the entire appliccation underneath angular CLI use webpack to bundel the javascript module ,when angular appliation ins build using `ng build --prod` there are same file are genearted to the folder to 'dist /appname'
3. the main entry point start executing :this file is a containor for all Angular application by default the exectuion is configured under the angular.json file it is main.js so every time the bootsrap proces is started from main of the config  
   
4. finaly ones we create ower own component we can import it to the app.module and create the tage into the template of the module and declare the selectoer name into @NgModule of the App module then it will render .

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
#### the emulated style of encapsulation is the concept of the compiler generate unique object attribute for each element to protect css leak betwen element tag
* There are two kinds of generated attributes:
1. An element that would be a shadow DOM host in native encapsulation has a generated _nghost attribute. 
This is typically the case for component host elements.
2. An element within a component's view has a _ngcontent attribute that identifies to which host's emulated shadow DOM this element belongs.
 
The exact values of these attributes aren't important. They are automatically generated and you should never refer to them in application code. But they are targeted by the generated component styles, which are in the <head> section of the DOM:

# Do your research on custom Web Components? What are they? and explain how the shadow DOM is important for creating custom Web Components.

Web Components is a suite of different technologies allowing you to create reusable custom elements — with their functionality encapsulated away from the rest of your code — and utilize them in your web apps

Web Components aims to solve such problems — it consists of three main technologies, which can be used together to create versatile custom elements with encapsulated functionality that can be reused.
1. Custom elements: A set of JavaScript APIs that allow you to define custom elements and their behavior, which can then be used as desired in your user interface.
2. Shadow DOM: A set of JavaScript APIs for attaching an encapsulated "shadow" DOM tree to an element — which is rendered separately from the main document DOM — and controlling associated functionality. In this way, you can keep an element's features private, so they can be scripted and styled without the fear of collision with other parts of the document
3. HTML templates: The <template> and <slot> elements enable you to write markup templates that are not displayed in the rendered page. These can then be reused multiple times as the basis of a custom element's structure

###  The basic approach for implementing a web component
1. Create a class in which you specify your web component functionality
2. Register your new custom element using the CustomElementRegistry.define() method, passing it the element name to be defined, the class or function in which its functionality is specified, and optionally, what element it inherits from 
3. If required, attach a shadow DOM to the custom element using Element.attachShadow() method. Add child elements, event listeners, etc., to the shadow DOM using regular DOM methods.
4. If required, define an HTML template using <template> and <slot>. Again use regular DOM methods to clone the template and attach it to your shadow DOM.
5. Use your custom element wherever you like on your page, just like you would any regular HTML element.

