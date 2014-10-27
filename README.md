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
            
            
// Here is the code to add to the class

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Shapes;
using Microsoft.Advertising.WinRT.UI;

namespace PracticeUIResize
{
    class ObjectResize
    {
        // Make sure to Get StartWidth on OnLoad to take as the second arguement when using this classes methods.
        //Methods
        // Resize Buttons and Sliders
        public void resizeButton(Control uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            Thickness uiElementPadding = uiElement.Padding;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
                // Set the padding divided by 3 to account for small text differences
                uiElementPadding.Left = uiElementPadding.Left * Ratio / 3;
                uiElementPadding.Right = uiElementPadding.Right * Ratio / 3;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
                // Set the padding divided by 2 to account for small text differences
                uiElementPadding.Top = uiElementPadding.Top * Ratio / 2;
                uiElementPadding.Bottom = uiElementPadding.Bottom * Ratio / 2;
            }
            uiElement.Padding = uiElementPadding;
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            if (font)
            {
                uiElement.FontSize = uiElement.FontSize * Ratio;
            }
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        // Resize TextBlocks(labels)
        public void resizeTextBlock(TextBlock uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            if (font)
            {
                uiElement.FontSize = uiElement.FontSize * Ratio;
            }
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        // Textboxes
        public void resizeTextBox(TextBox uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                //uiElement.Width = uiElement.Width * Ratio;
                uiElement.Width = uiElement.Width * Ratio;
                uiElement.MinWidth = uiElement.MinWidth * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
                uiElement.MinHeight = uiElement.MinHeight * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            if (font)
            {
                uiElement.FontSize = uiElement.FontSize * Ratio;
            }
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        // Resize Images
        public void resizeImage(Image uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        // Ink Canvas
        // Images
        public void resizeCanvas(Canvas uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        public void resizeShape(Shape uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        public void resizeGrid(Grid uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
        // Resize Ad does not actually resize but hides on resize and reappears full screen
        public void resizeAd(AdControl uiElement, Double StartWidth, bool width, bool height, bool font)
        {
            Double WindowWidth = Window.Current.Bounds.Width;
            Double Ratio = WindowWidth / StartWidth;
            if (width)
            {
                uiElement.Width = uiElement.Width * Ratio;
            }
            if (height)
            {
                uiElement.Height = uiElement.Height * Ratio;
            }
            // Get Margin
            Thickness uiElementMargin = uiElement.Margin;
            uiElementMargin.Left = uiElementMargin.Left * Ratio;
            uiElementMargin.Top = uiElementMargin.Top * Ratio;
            uiElement.Margin = uiElementMargin;
            // Add StartWidth = Window.Current.Bounds.Width; after method to reset start size.
        }
    }
}

            
            
