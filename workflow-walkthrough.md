# Workspace and Framworks

##  Creating a framework for iOS

![startProject](../master/assets/sketch1.gif)  

### Description
you will learn how to build an iOs framwork, you can sahre code between apps, modularize your cose, distribute it as a third-party library  


## Steps

### Create a framework  iOS ▸ Framework & Library ▸ Cocoa Touch Framework.  
![startProject](../master/assets/image1.png)

### copy all file what you need, use the option **show in finder**   

### Buld and quiet the xcode and run again  

### Import the framework  `nameFramework.xcodeproj`  

### Embed Your Binary
The project needs to see the framework **link the framework to the app’s target**  
`nameModule.framework`  : This file is the output of the framework project that packages up the binary code, headers, resources and metadata.  
You just added an entry for the framework in both Embedded Binaries and Linked Frameworks and Binaries.  

### Access control
This is because Swift uses access control to let you determine whether constructs are visible to other files or modules.  

Swift has five levels of access control. Use the following rules of thumb when creating your own frameworks:  

`Open and public`: for code called by the app or other frameworks, e.g. a custom view.  
`Internal`: for code used between functions and classes within the framework, e.g. custom layers in that view.  
`Fileprivate`: for code used within a single file, e.g. a helper function that computes layout heights.  
`Private:` for code used within an enclosing declaration, such as a single class block, and extensions of that declaration in the same file.  

1.   
```swift 

import UIKit
import CoreData
import Checkbox  // custom framework

class ShortcutsViewController: UIViewController {}
```
2.  

```swift 

import UIKit

// Public Access Control
public protocol CheckboxDelegate {
  func checkBox(checkBox: Checkbox, userChecked: Filter)
}

// Public Access Control
public class Checkbox: UIView {
  
  public var isChecked: Filter = .none {
    didSet {
      updateAppearance()
    }
  }
  
  var checkmarkImageView: UIImageView!
  
  // Public Access Control
  public var delegate: CheckboxDelegate?
  
  // Public Access Control
  public required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)
    commonInit()
    updateAppearance()
  }
  ...
} 
```
### Update the Storyboard

**Update the storyboard by telling it where to find the custom view**

![startProject](../master/assets/image2.png)





