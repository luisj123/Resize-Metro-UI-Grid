Resize-Metro-UI-Grid
====================

Resize XAML elements dynamically C# Metro Apps Windows 10

This class works best if all of your UI elements are within a single grid and aligned top and left.

Instructions:
To use this class create an instance of the class in C# file you want to use it in
(ex. ObjectResize resize = new ObjectResize();).   For apps with single page navigation set a start width variable immediately following the Initialize Componet(ex.  StartWidth = Window.Current.Bounds.Width;).   For best results run any ObjectResize methods immediate following the StartWidth Initalization and then again in the Window.Current.SizeChanged event.  Remember to reset the start width after running the methods.  

If you have multiple pages in your app you may wish to save the screen width in the App.cs in the OnLaunce Metd ex.                     // Save the original screen size on load.
            var localSettings = Windows.Storage.ApplicationData.Current.LocalSettings;
            localSettings.Values["screenWidth"] = Window.Current.Bounds.Width.ToString();
Then reload this data after teh InitalizeComponent in your class.
            var localSettings = Windows.Storage.ApplicationData.Current.LocalSettings;
            try { StartWidth = Double.Parse(localSettings.Values["screenWidth"].ToString()); }
            catch { StartWidth = Window.Current.Bounds.Width; }
            
            
