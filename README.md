# Angular lifecycle hooks? 
 The lifecycle continues with change detection, as Angular checks to see when data-bound properties change, and updates both the view and the component instance as needed. The lifecycle ends when Angular destroys the component instance and removes its rendered template from the DOM.
 ### lifecycle hook
is An interface that allows you to tap into the lifecycle of directives and components as they are created, updated, and destroyed.

## Angular calls these hook methods in the following order:

1. ngOnChanges: When an input/output binding value changes.
2. ngOnInit: After the first ngOnChanges.
3. ngDoCheck: Developer's custom change detection.
4. ngAfterContentInit: After component content initialized.
5. ngAfterContentChecked: After every check of component content.
6. ngAfterViewInit: After a component's views are initialized.
7. ngAfterViewChecked: After every check of a component's views.
8. ngOnDestroy: Just before the directive is destroyed

#### ngOnChanges() : 
Respond when Angular sets or resets data-bound input properties.Respond when Angular sets or resets data-bound input properties. The method receives a SimpleChanges object of current and previous property values.
Note that this happens very frequently, so any operation you perform here impacts performance significantly.

Note that if your component has no inputs or you use it without providing any inputs, the framework will not call ngOnChanges()
####  ngOnInit
Initialize the directive or component after Angular first displays the data-bound properties and sets the directive or component's input properties.
Called once, after the first ngOnChanges().

#### ngDoCheck()
Detect and act upon changes that Angular can't or won't detect on its own.
Called immediately after ngOnChanges() on every change detection run, and immediately after ngOnInit() on the first run.
#### ngAfterContentInit()
Respond after Angular projects external content into the component's view, or into the view that a directive is in.
Called once after the first ngDoCheck().

#### ngAfterContentChecked()
	
Respond after Angular checks the content projected into the directive or component.
Called after ngAfterContentInit() and every subsequent ngDoCheck().

#### ngAfterViewInit()
	
Respond after Angular initializes the component's views and child views, or the view that contains the directive.
Called once after the first ngAfterContentChecked().
#### ngAfterViewChecked()
Respond after Angular checks the component's views and child views, or the view that contains the directive.
Called after the ngAfterViewInit() and every subsequent ngAfterContentChecked().

#### ngOnDestroy()
Cleanup just before Angular destroys the directive or component. Unsubscribe Observables and detach event handlers to avoid memory leaks.
Called immediately before Angular destroys the directive or component.
