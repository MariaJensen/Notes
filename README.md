# Notes
Things I must not forget

When an event is emitted from somewhere in the window object, an event object is created. Let event be such an object. 

* event.type is a string, which is the name of the event. 'click' for example. 

* event.target is the EventTarget object on which the event was fired. A button element for example. 

Consider now all the ancestors of event.target. On top of the hierachy is the window object, then all other ancestors of event.target in descending order, and lastly the event.target itself. 

After the event has been emitted and the event object created, the event object will be propagated among the ancestors of event.target in a number of phases. 

* Capturing phase: The event object is propagated through the ancestors of event.target in descending order, starting with the window object and ending with the parent of event.target. 
At each ancestor all eventlisteners for event.type registered on event.target are executed, regardless of if capture=true or not. 
