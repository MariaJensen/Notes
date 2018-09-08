# Events in the window object model

When an event is emitted from somewhere in the window object, an event object is created. Let `event` be such an object. 

* **`event.type`** is a string, which is the name of the event. 'click' for example. 

* **`event.target`** is the EventTarget object on which the event was fired. A button element for example. 

Consider now all the ancestors of `event.target`. On top of the hierachy is the window object, then all other ancestors of event.target in descending order, and lastly the `event.target` itself. 

After the event has been emitted and the event object created, the event object will be propagated among the ancestors of `event.target` in a number of phases: 

* **Capturing phase:** The event object is propagated through the ancestors of `event.target` in descending order, starting with the window object and ending with the parent of `event.target`. 

  At each ancestor all event listeners for `event.type` registered on the ancestor with `capture=true` are executed. 
  
* **Target phase:** All event listeners for `event.type` registered on event.target are executed, regardless of if `capture=true` or not. 

If `**event.bubbles**=false`, propagation will end after the target phase. Otherwise the bubbling phase will take place: 

* **Bubbling phase:** The event object is propagated through the ancestors of `event.target` in ascending order, starting with the parent of `event.target` and ending with the window object. 

  At each ancestor all event listeners for `event.type` registered on the ancestor with `capture=false` are executed. 
  
During the propagation `event.eventPhase` holds the phase that is currently taking place, and `event.currentTarget` holds the anscestor whose event listeners are currently being executed. 

* `event.composedPath()`: todo

* `event.stopPropagation()` will wait until all listeners for event.type on the current target in the current phase are done, then cancel further propagation. 

* `event.stopImmediatePropagation()` will wait until the current listener for event.type on the current target in the current phase is done, then cancel further propagation. 

* `event.cancelable`: todo

* `event.preventDefault()`: todo

* `event.defaultPrevented`: todo

* `event.composed`: todo

* `event.isTrusted`: todo

* `event.timeStamp`: todo
