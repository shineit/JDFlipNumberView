JDFlipNumberView
------------------

See [screenshots](#screenshots) below.

The Flip Number View is simulating an analog flip display (like those for the departure time on the airport).

It is using CoreAnimation to get the desired effect. It's well abstracted and should be really easy to use. But it still needs some work, so feel free to contribute!

## Contents

You get three classes for different usecases:

- `JDFlipNumberView`  
  __A single animated digit.__ Range 0-9.
- `JDGroupedFlipNumberView`  
  A grouped and chained choosable number of flipviews for higher numbers.  
  It is using a variable amount of `JDFlipNumberView` instances itself and chains them together.
- `JDDateCountdownFlipView`  
  __A date countdown.__ Just init with a target date and add it as a subview.  
  It is using four `JDGroupedFlipNumberView` instances itself and chains them together.
  
  ![Caution Sign](http://upload.wikimedia.org/wikipedia/en/thumb/f/f7/Nuvola_apps_important.svg/50px-Nuvola_apps_important.svg.png "Caution Sign")  
  __Note:__ The `JDDateCountdownFlipView` is not yet production ready, because the `maximumValue` of the `JDGroupedFlipNumberView` is interpreted wrong. Don't use a maximum value on grouped flipViews and don't use the Date Countdown at all for now, because it behaves buggy. I'm trying to fix these bugs _ASAP_. (You may follow the progress via the issues and the branches other than master.)

## How to use

Recommend: Use [cocoapods] to install it.  

(OR add all files from `JDFlipNumberView/JDFlipNumberView/` manually to your project, including the `JDFlipNumberView.bundle`.  
And you also need to link the `QuartzCore.framework`)

In any case, after installing, you only need to follow these three steps, to use it:

> 1. Init the class
> 2. Set an int value (or a date)
> 3. Start the animation

__Example:__ A countdown view from 1000 seconds to 0.

    JDGroupedFlipNumberView *flipNumberView = [[JDGroupedFlipNumberView alloc] initWithFlipNumberViewCount: 4];
    flipNumberView.intValue = 1000;
    [flipNumberView animateDownWithTimeInterval: 1.0];
    
    [self.view addSubview: flipNumberView];
    flipNumberView.frame = CGRectMake(10,100,300,100);

That's it.  
This will display a working, flipping, animating countdown view!

## How to start the animation?

Use any of the following methods:

    // basic animation
    - (void) animateToNextNumber;
    - (void) animateToPreviousNumber;
    
    // timed animation
    - (void) animateUpWithTimeInterval: (NSTimeInterval) timeInterval;
    - (void) animateDownWithTimeInterval: (NSTimeInterval) timeInterval;


## Do you use the JDFlipNumberView?

Feel free to add your app to the
[wiki](https://github.com/jaydee3/JDFlipNumberView/wiki/Apps-using-JDFlipNumberView).

## Screenshots

![Overview](https://raw.github.com/jaydee3/JDFlipNumberView/master/Screenshots/menu.png "Overview")

![Single Digit](https://raw.github.com/jaydee3/JDFlipNumberView/master/Screenshots/singledigit.png "Single Digit")

![Date Countdown](https://raw.github.com/jaydee3/JDFlipNumberView/master/Screenshots/datecountdown.png "Date Countdown")


[cocoapods]: https://github.com/CocoaPods/CocoaPods/

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/015f5826a4c4d785736b35a0ae7568ce "githalytics.com")](http://githalytics.com/jaydee3/JDFlipNumberView)