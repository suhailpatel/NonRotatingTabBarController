NonRotatingTabBarController
===========================

Code to help solve an issue in iOS Development where you want all your views in your tab bar controller to be a specific orientation (such as Portrait) but have a single view or subview in one of your tabs which require a different orientation (such as Landscape) which the rest of your views don't support

This became an issue in iOS6 SDK because you can no longer set an orientation but still use other orientations which you haven't mark as supported (they now crash the app with a crash log message).

Usage
-----

Simply include the NonRotatingTabBarController.h class and initialise your tab bar controller as normal but using NonRotatingTabBarController

    self.tabBarController = [[NonRotatingTabBarController alloc] init]; // or whatever initialising tab bar code you have
    
Now all your views will be portrait by default unless you specify in your view to use landscape for example (there are a whole bunch of combinations so modify it as you please and don't forget to modify the included files too!)

    - (BOOL)shouldAutorotateToInterfaceOrientation:(UIInterfaceOrientation)interfaceOrientation 
    {
        return (interfaceOrientation == UIInterfaceOrientationLandscapeLeft || interfaceOrientation == UIInterfaceOrientationLandscapeRight);
    }

    - (NSUInteger)supportedInterfaceOrientations 
    {
        return UIInterfaceOrientationMaskLandscape;
    }
  
Also be sure to specify in your project settings ALL the orientations you use in your app otherwise it WILL crash in iOS6, let the code handle the rotation enabled/disabled

![Xcode Project Settings][1]

  [1]: http://i.stack.imgur.com/RZUOZ.jpg

License
-------

Copyright (C) 2012 Suhail Patel

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.