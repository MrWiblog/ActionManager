ActionManager
=============

ActionManager is an open-source system to run custom code at defined points in your .NET applications, without know where (or even if) those points occur. ActionManager is modelled on WordPress' Plugin API.

ActionManager runs actions called, amazingly, Actions.  To 'hook' your method into an Action an ActionMethod (after first adding a reference to the stillbreathing.co.uk.ActionManager DLL, and optionally add a using statement at the top of your page). Each ActionMethod can be created with a single line of code:

`ActionMethod MyMethod = new ActionMethod("Namespace.Class.Method");`

There are two overloads for the ActionMethod class. The first accepts a boolean parameter to set whether the target class/method is static (and therefore does not need to be instantiated):

`ActionMethod MyMethod = new ActionMethod("Namespace.Class.Method", true);`

The second overload adds another boolean parameter to set whether the target method accepts an object parameter. The object parameter can be modified and returned to the calling Action:

`ActionMethod MyMethod = new ActionMethod("Namespace.Class.Method", true, true);`

Then add the ActionMethod to the Action using the ActionManager.AddMethod() method. This call to ActionManager.AddMethod() means that whenever the 'MyAction' action occurs, the ActionMethod defined in 'MyMethod' will be executed:

`ActionManager.AddMethod("MyAction", MyMethod);`

You can also set a priority for the ActionMethod; higher numbers mean the ActionMethod will run before other ActionMethods for this Action with a lower priority:

`ActionManager.AddMethod("MyAction", MyMethod, 1000);`

ActionMethod properties
-----------------------

The following properties can be set for a ActionMethod:

* **ActionName** (string): The name of the action this method will be called for
* **Priority** (int, default 0): The priority of this method, higher numbers are executed first
* **IsStatic** (boolean, default true): Whether this method is static, or needs instantiating
* **AssemblyName** (string): The name of the assembly containing this method
* **Namespace** (string): The namespace of this class
* **ClassName** (string): The name of the class to be called
* **MethodName** (string): The name of the method to be called
* **AcceptsParameters** (boolean, default false): Whether this method accepts parameters and returns an object
* **ThrowOnException** (boolean, default false): Whether to throw exceptions occurring in this method

Licencing
---------

ActionManager is released under any of the following licenses, please choose the one you wish to use:

* [Creative Commons Attribution-ShareAlike 3.0 licence](http://creativecommons.org/licenses/by-sa/3.0/)
* [Microsoft Public License](http://www.opensource.org/licenses/ms-pl.html)
* [MIT License](http://www.opensource.org/licenses/mit-license.php)
* [BSD License](http://www.opensource.org/licenses/bsd-license.php)