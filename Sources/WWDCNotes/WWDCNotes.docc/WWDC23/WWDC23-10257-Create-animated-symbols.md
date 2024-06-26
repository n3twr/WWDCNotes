# Create animated symbols

Discover animation presets and learn how to use them with SF Symbols and custom symbols. We’ll show you how to experiment with different options and configurations to find the perfect animation for your app. Learn how to update custom symbols for animation using annotation features, find out how to modify your custom symbols with symbol components, and explore the redesigned export process to help keep symbols looking great on all platforms.

@Metadata {
   @TitleHeading("WWDC23")
   @PageKind(sampleCode)
   @CallToAction(url: "https://developer.apple.com/wwdc23/10257", purpose: link, label: "Watch Video (18 min)")

   @Contributors {
      @GitHubUser(multitudes)
   }
}



## Chapters
[1:51 - Previewing Animations](https://developer.apple.com/videos/play/wwdc2023/10257/?time=111)  
[4:25 - Animating custom symbols](https://developer.apple.com/videos/play/wwdc2023/10257/?time=265)  
[7:59 - Symbol components](https://developer.apple.com/videos/play/wwdc2023/10257/?time=479)  
[14:50 - Compatibility](https://developer.apple.com/videos/play/wwdc2023/10257/?time=890)

## Intro

- Previewing animations
- Animating custom symbols
- Symbol components
- Compatibility

![SF Symbols][symbols1]  

[symbols1]: WWDC23-10257-symbols1

SF Symbols have been a huge part of what makes Apple platforms look and feel the way they do.

![SF Symbols][symbols2]  

[symbols2]: WWDC23-10257-symbols2

There are thousands of symbols built into Apple's platforms, sharing common visual designs and behaviors. Symbols are customizable.

![SF Symbols][symbols3]  

[symbols3]: WWDC23-10257-symbols3

Symbols can communicate complex concepts in a small amount of screen real estate.

![SF Symbols][symbols4]  

[symbols4]: WWDC23-10257-symbols4

With SF Symbols 5, symbols get a whole new dimension.

![SF Symbols][symbols5]  

[symbols5]: WWDC23-10257-symbols5


# Previewing animations


Taking a look at some examples.

![Previewing animations][animations1]  

[animations1]: WWDC23-10257-animations1

There is a new tab here in the sidebar. This is the animation inspector, and can be used to preview the new animation effects.

![Previewing animations][animations2]  

[animations2]: WWDC23-10257-animations2

Selecting the new animation effects from this pop up button like the Bounce animation. Hitting the preview button, the animation plays in the main Gallery view, as well as in the symbol row below it and the preview area in the sidebar. Around the preview button, there are controls for configuring the animation. Choose options like whether the symbol should bounce upwards or downwards, and whether the layers of the symbol will bounce separately or if the whole symbol should bounce at once.

Changing some of these settings, the label under the preview area went from “Automatic” to "Modified." Writing code for an app, every animation type comes with default settings pre-selected, and we will see the word "Automatic". Click the reset button to get back to the defaults.

Click this button to copy the name of the effect we'll need for the Swift or Objective-C APIs.

![Previewing animations][animations3]  

[animations3]: WWDC23-10257-animations3

This speaker symbol also supports variable color.

With the Cumulative option selected, the variable color layers activate gradually, then all fade out together. With Iterative, only one layer activates at a time. And there is the Reversing option as well.

# Animating custom symbols

Let's update last year's custom symbols and getting them ready for animation.

Here's a 3x3 cube symbol, annotated for Hierarchical and Multicolor rendering, and the front face is broken into different layers so to apply variable color. It supports the variable color animation right out of the box.

![Previewing animations][animations4]  

[animations4]: WWDC23-10257-animations4

There's a new control in the annotation list that allows to specify which layers should pulse when using the By Layer setting. If none of the layers in the symbol are marked, the whole symbol will pulse. Let's mark all of the layers that make up the front face to pulse, and preview again.

![Previewing animations][animations5]  

[animations5]: WWDC23-10257-animations5

Motion. Symbols that were exported from version 4 or earlier of the SF Symbols app, or exported to be compatible with Xcode 14, won't include motion information, and will always move as a whole symbol. But let's see what happens when we are exporting from this version of the SF Symbols app, version 5, for use in Xcode 15.

Going back to the Bounce animation and playing it with the puzzle cube symbol.

By default, every layer in a symbol will move independently when By Layer is selected.
There is a new feature in annotation. We can now create groups of layers that can animate all of their sublayers together. Select all of the layers that make up the front face and add them to a new layer group.

Inside of a layer group, all of the layers still keep their own annotations and settings, but now they all move together.

Now there's less motion. let's undo and select all of the layers of the symbol and add them all to a single group.

The different faces of a cube don't really move separately. By grouping all of these layers together, the cube will always animate as a single unit, even if the code requests by layer.

This circular enclosure is a common design element in SF Symbols. 

![Previewing animations][animations6]  

[animations6]: WWDC23-10257-animations6

There are lots of symbols in the built-in library that use a similar circular treatment, and the consistency is one of the key things that makes SF Symbols instantly recognizable and familiar.

![Previewing animations][animations7]  

[animations7]: WWDC23-10257-animations7

Custom symbols should try to match these treatments too.

# Symbol components

A symbol component provides artwork and behavior that looks and feels like a system-provided SF Symbol. We take one of our custom symbols and combine it with a symbol component to get a new symbol.

![Previewing animations][animations8]  

[animations8]: WWDC23-10257-animations8

Look through the library of components and choose which ones we want to use. There are enclosures, badges, and a slash component.

![Previewing animations][animations8]  

[animations8]: WWDC23-10257-animations8

These new symbols have appeared in the custom symbols library.

And the .circle.fill version is already set up...

Now, we'll also want to make sure our new symbol looks great in all of the different scales and weights that symbols support. With three scales and nine weights, that's a total of 27 different variations.

![Previewing animations][animations10]  

[animations10]: WWDC23-10257-animations10

Symbol components are powered by variable templates, which take care of most of the work for us.

![Previewing animations][animations11]  

[animations11]: WWDC23-10257-animations11

Variable templates were introduced in SF Symbols 3; we only need to provide three drawings in the Small scale: one each for the Ultralight, Regular, and Black weights. Then, as long at the bezier paths used in each drawing are compatible, the system can mix the drawings together to create the remaining 24 possible variants.

![Previewing animations][animations12]  

[animations12]: WWDC23-10257-animations12

There's a set of previews at the top of the Gallery view...

Usually, we'll only need to make adjustments to the Regular weight, but we can click the Override checkbox in the Ultralight or Black weights and make additional adjustments. The system will take these new adjustments into account when automatically creating in-between weights like Semibold.  
As the base symbol is scaled down to fit in the enclosure, the system is using the base symbol's variable template to apply weight compensation, increasing the weight and thickness of the symbol as its size decreases; 

![Previewing animations][animations13]  

[animations13]: WWDC23-10257-animations13

this helps to keep it looking consistent with both its larger, non-enclosed version and with the circle surrounding it. And like many other parts of symbol components, we can do additional fine-tuning to the enclosed symbol's weight to get the final visual result we want.

### Symbol components recap
- Custom symbols can be combined with components to create new symbols
- Base custom symbols must use variable templates
- Overrides in variable templates are ignored
- Editable templates cannot be exported from symbols created with components

There are more than 40 components included in the SF Symbols app this year.

![Previewing animations][animations14]  

[animations14]: WWDC23-10257-animations14

# Compatibility

When exporting an editable template to modify a symbol's shape and structure, we'll now see a wireframe view, instead of the filled shapes that were previously shown in templates.

![Compatibility][compatibility]  

[compatibility]: WWDC23-10257-compatibility

Symbols that are optimized for motion often include shapes that are used to erase portions of other shapes during rendering. Therefore the wireframe will help.
There's also a new Compatibility picker exporting a template. And if we're targeting older platforms, the SF Symbols app will give us a template that better suits that platform. For example, targeting SF Symbols 3, which corresponds to iOS 15 and macOS Monterey, we'll get a simpler drawing that isn't optimized for motion, because the layer structures we use for motion weren't fully supported in SF Symbols 3. 

And targeting SF Symbols 2, which corresponds to iOS 14 and macOS Big Sur, we'll automatically get a static template, because variable templates were introduced in SF Symbols 3. 

![Compatibility][compatibility1]  

[compatibility1]: WWDC23-10257-compatibility1

The same concepts apply when annotating custom symbols. For example, choosing SF Symbols 3 or earlier, we are no longer able to edit the monochrome annotation of the symbol, because monochrome annotations weren't customizable until SF Symbols 4.

When the symbol is ready to be exported for Xcode, we tell the app what version of Xcode we are using and it will choose the best file format to export.

![Compatibility][compatibility2]  

[compatibility2]: WWDC23-10257-compatibility2

# Resources

[Have a question? Ask with tag wwdc2023-10257](https://developer.apple.com/forums/create/question?&tag1=318&tag2=703030)  
[Search the forums for tag wwdc2023-10257](https://developer.apple.com/forums/tags/wwdc2023-10257)

# Related Videos
[Animate symbols in your app -  WWDC23](https://developer.apple.com/videos/play/wwdc2023/10258)  
[What’s new in SF Symbols 5 - WWDC23](https://developer.apple.com/videos/play/wwdc2023/10197)
