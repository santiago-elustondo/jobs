


* Input-Output
    * Main Demo: augury-examples/input-output
    * Sub Features
        * Once Augury is opened, the component view is presented in the Component Tree. It shows all the available components in the application, and regular DOM elements depending on selected Component Rendering Mode. The properties displayed with each element/component are the ones managed by angular (the ones set with an “[...]” directive)
        * Hovering over a component in tree view displays a selector over the component’s output on the page.
        * If we select a component inside the Component Tree, to the left inside the Properties tab we see the component's properties under the State group. (Augury will not show properties in a component if it not assigned a value, since TypeScript will simply compile it out.)
        * Selected Component will be available under the global “$$el” variable as an Angular `DebugElement `(`DebugElement` is an Angular2 class that contains all kinds of references and methods relevant to investigate an element or component)
        * In the Properties tab, under State, an editable property will be displayed with a dashed underline. We can edit these by clicking and typing. 
        * To jump to the source code of a selected component, click on the View Source link, it is located in the Properties tab.
* Routes 
    * Main Demo: augury-examples/routes
    * Sub Features
        * The Component Tree shows instances of router-outlet as a child element
        * Updating the selected route (by clicking on a Router Link or updating URL) updates the Component Tree view.
        * The Router Tree tab will show all the defined routes that are currently loaded in the application. It shows the path to each component.
        * Hovering over a node in the Router Tree opens an informational dialog with the following info:
            * Path: the route’s url
            * Handler: 
                * one of: 
                    * Name of top-level Component at that route
                    * “No-name”
                    * ?? what about lazy routes ??
            * Data: ????
        * Lazy loaded paths will have a node marked with a “[Lazy]” suffix.
        * Lazy loaded routes appear on the Router Tree after being loaded in (by entering that route).


# Dependency Injection

Main Demo: augury-examples/dependency-injection


## Component Rendering Mode



1. Select the 3-dotted button next to Angular version number. A menu should appear.
2. Select “Hybrid View” from the menu.

    In the Component Tree, 

1. Angular Components should display.
2. Native elements should appear if they contain properties set by the Angular application. Clicking on such element should display items in the Properties tab.
3. Select “All components and elements” from the menu.

    In the Component Tree,

1. Should display all Angular Components and native HTML elements (both that have properties set by the Angular application and those that don’t). HTML elements that don’t have properties set by Angular shouldn’t have any properties set in the Properties tab.
4. Select “Components only” from the me
    1. Should only display Angular application Components.


## Dependency

In the Component Tree, select an Angular Component that has a Dependency that’s injected. In the Properties tab, the Dependency should be listed under the Dependencies section, and its corresponding component property listed under the State section.


## Injector Graph

*Injector Graph* tab located next to the *Properties *tab. If we select it, we will see a dependency tree for a selected component in the Component Tree. In the Injector Graph,



1. The root should be at the very top (blue circle) and labelled.
2. Arrows followed by circles should follow down the component tree to the component selected.
3. A red line should be connected to the component circle representing where the dependency is being injected. The other end of the red line should be a red circle with the name of the dependency that the component depends on.
4. If the Dependency (red circle) is not set as a provider on the Angular Component that requires that Dependency, there should be a dotted line connecting the Dependency to its Parent Injector.


# Modules List

Main Demo: augury-examples/modules

When the DevTools panel opens, select the Augury tab located on the far right. By default the *Component Tree* tab will be open. To the far right, there will be a tab labeled *NgModules*. Click on this Tab.



1. Here we can see what *imports*, *exports*, *providers*, *declarations*, and *providers in declarations* are found in the module
2. 