# Which routers exist in a native Magento implementation?

admin, standard and default

# How does the standard router map a request to a controller class?

All of the routers mentioned above have a 'match()' method that is responsible for associating a URL to a controller action.
The standard router's 'match()' method breaks the request path into 3 parts by slash.
The first part corresponds to a module name, the second part is the controller and the third is the method.
This is how the standard router maps a URL to a controller class.

# How does the standard router build the filesystem path to a file that might contain a matching action controller?

The 'getControllerFileName()' method is used. This method can convert a controller Magento path into a directory path by, essentially, making a few changes such as swapping underscores with directory seperators.
For example, Test_Foo is converted to Test/Foo.php

# How does Magento process requests that cannot be mapped?

Requests that don't get mapped to any router end up being handle by the default router, which redirects to a 404 page or a noRoute page.

# After a matching action controller is found, what steps occur before the action method is executed?

Module, Controller and Action names are set. 'SetControllerModule' is also set to the found module name. URL parameters are added to the request and finally the request is set to dispatch = true