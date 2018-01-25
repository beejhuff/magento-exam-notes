## Which ways exist to specify the layout update handles that will be processed during a request?

1. In a controller action when we call the 'loadLayout()' function we can pass different handles as variables. E.g.
    
        $this->loadLayout(array('handle1','handle2','default');
        
2. Or from anywhere else, the following function can be used.

        $this->getLayout()->getUpdate()->addHandle('handle3');

3. Finally, we can specify in the layout XML file:

        <reference name="root">
            <update handle="removeFooter" />
        </reference>

        <removeFooter>
            <remove name="footer" />
        </removeFooter>

## Which classes are responsible for the layout being loaded?

- Mage_Core_Controller_Front_Action
- Mage_Core_Controller_Varien_Action
- Mage_Core_Model_Layout
- Mage_Core_Model_Layout_Handle
- Mage_Core_Model_Layout_Element

## How are layout xml directives processed?

Mage_Core_Controller_Varien_Action::loadLayout() – This in turn calls “generateLayoutBlocks()” function. This function calls “generateBlocks()” function in “Mage_Core_Model_Layout” class which processes the entire layout xml blocks, references etc and creates block objects from xml.

## Which configuration adds a file containing layout xml updates to a module?

Modules config.xml

      <frontend>
        <layout>
            <updates>
                <catalog>
                    <file>catalog.xml</file>
                </catalog>
            </updates>
        </layout>


## Why is the load order of layout xml files important?

All layout files are merged into one XML object Mage_Core_Model_Layout_Element.
The later the file is loaded, the less chance it will be overridden by another layout.xml file.

This is why local.xml is loaded last or as of 1.9 the themes.xml file/files.