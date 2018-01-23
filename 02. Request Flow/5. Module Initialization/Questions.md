## 1. What does "Magento loads modules" mean?

In short, loading all of the declared, active modules inside of the 'app/etc/modules' directory.
Modules are subsequently sorted based on dependencies. The modules configuration is directly added to the config tree. 

1. app/etc/modules/
2. Sort modules
3. config.xml is loaded and added to config tree

## 2. In which order are Magento modules loaded?

Magento modules are loaded according to their .xml files, in this order:

1. Mage_All.xml
2. Mage_*.xml files
3. Any other xml files

If Module A, for example, depends on Module B then Module B will be loaded first.

## 3. Which core class loads modules?

Mage_Core_Model_Config

## 4. What are the consequences of one module depending on another module?

The dependency module must be loaded and exist or it will cause Magento to throw an exception.

## 5. During the initialization of Magento, when are modules loaded in?

The 'initModules()' is called within the 'Mage_Core_Model_App' class.
They are loaded before Front Controller Dispatch and after caching has been checked.

## 6. Why is the load order important?

Dependencies and core functionality

Core functionality needs to be loaded first, and dependencies need to be loaded before the modules that depend on them.

## 7. What is the difference regarding module loading between Mage::run() and Mage::app()?

**Note:** Important.

Mage::app() – Initialize application without request processing.
Mage::run() – Run application. Run process responsible for request processing and sending response.

Essentially, 'Mage::app()' doesn't do any request processing e.g. '$this->getFrontController()->dispatch()' is missing. 