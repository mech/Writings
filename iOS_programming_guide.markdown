# iOS Programming Guide

## View Controller
There are 3 categories of view controllers:
- **Custom view controller** (e.g. UITableViewController and LeaveApplicationViewController)
- **Container view controller** (e.g. UINavigationController, UITabBarController, UISplitViewController)
- **Modal view controller**

### UINavigationController
Use to present hierarchical information. In iOS 3, added a new navigation toolbar. The term **Navigation Interface** is used to describe the whole screen you see which include navigation bar, optionally the navigation toolbar and the custom content.

The navigation stack is a last-in, first-out collection of custom view controller objects that is managed by the navigation controller.

First controller in the stack is the **Root View Controller** and cannot be removed!

Your main responsibility is to push new view controllers onto the stack in response to user actions.

There are many points in your code to create navigation controller:
1. If the navigation controller provides the root view for your application window, do it at applicationDidFinishLaunching:
2. If you present the navigation controller modally, it is simpler to create it at the point of use, present it, and then release it when it is no longer needed.
3. If it reside in a UITabBarController, just prepare it and release it when added to the array.

LeaveRootViewController *rootController = [[LeaveRootViewController alloc] initWithContractCode:@"S6414.01"];

leaveNavigationController = [[UINavigationController alloc] initWithRootViewController:rootController];

[rootController release];

#### Delegate Object for UINavigationController
If you want to respond to notifications from the navigation controller, you can provide a delegate object.

You usually use willShowViewController to save any editing to your application's data model.

#### Customizing UINavigationBar
A navigation bar is a container for content. The content is provided by one or more UINavigationItem objects stored in the **navigation item stack**.

The owner of the navigation bar is responsible for pushing items onto the stack and popping them off as needed. Most of the navigation bar's content is obtained from the topmost navigation item, a pointer to the back item is maintained so that a back button can be created.

Each view controller actually provides its own navigation item.

Navigation bar has 3 positions for placing items and they can be obtained from UINavigationItem:
1. Left - backBarButtonItem and leftBarButtonItem. You can replace the back button by assigning a UIBarButtonItem object to the leftBarButtonItem property.
2. Center - titleView. You can have custom view.
3. Right - rightBarButtonItem

UISegmentedControl *sc = [[UISegmentedControl alloc] initWithItems:[NSArray arrayWithObjects:[UIImage imageNamed:@"up.png"], [UIImage imagedNamed:@"down.png"], nil]];

[sc addTarget:self action:@selector(segmentAction:) forControlEvents:UIControlEventValueChanged];
sc.frame = CGRectMake(0, 0, 90, kCustomButtonHeight);
sc.segmentedControlStyle = UISegmentedControlStyleBar;
sc.momentary = YES;

defaultTintColor = [sc.tintColor retain];

UIBarButtonItem *segmentBarItem = [[UIBarButtonItem alloc] initWithCustomView:sc];
[sc release];

self.navigationItem.rightBarButtonItem = segmentBarItem;
[segmentBarItem release];

### UITabBarController

### Modal View Controller
Interrupt the current workflow and display a new set of views.

## Model


## Core Data
NSManagedObject is the entity object.

### Key Value Coding
A way to access the attributes of an object without calling the accessors directly.

-valueForKey:
-setValue:forKey:

By itself, this is not all that useful. However, there are huge benefits to it that are not apparent on the surface.

### Key Value Observing
KVO allows us to request notifications when an attribute has changed.

-addObserver:forKeyPath:options:context
-removeObserver:forKeyPath:

[model addObserver:myTextField forKeyPath:@"name" options:(NSKeyValueObservingOptionNew|NSKeyValueObservingOptionOld) context:kJoblineObserver];

Any time a property the view's components are observing changed, the -observeValueForKeyPath:ofObject:change:context is called.

KVO is what allows views to automatically refresh themselves from the model when the data has changed.


## Networking
### Path
NSURL *path = [NSURL fileURLWithPath:@"/Users/"];
NSURL *path = [NSURL URLWithString:@"file:///Users/"];

