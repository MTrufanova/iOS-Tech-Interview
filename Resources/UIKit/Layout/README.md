### [iOS Tech Interview](https://github.com/venvear/iOS-Tech-Interview/blob/master/README.md)

## Contraint

The relationship between two user interface objects that must be satisfied by the constraint-based layout system.
Each constraint is a linear equation with the following format:
item1.attribute1 = multiplier × item2.attribute2 + constant


## AutoLayout

Auto Layout dynamically calculates the size and position of all the views in your view hierarchy, based on constraints placed on those views.

It is a constraint-based layout system that allows developers to create an adaptive interface, that responds appropriately to changes in screen size and device orientation.

After solving for the required constraints, Auto Layout tries to solve all the optional constraints in priority order from highest to lowest. This combination of inequalities, equalities, and priorities gives you a great amount of flexibility and power. 


## AutoLayout guide

The purpose of a **strong** reference is to keep an object alive. Str

## SafeArea

Safe areas help you place your views within the visible portion of the overall interface. UIKit-defined view controllers may position special views on top of your content. For example, a navigation controller displays a navigation bar on top of the underlying view controller’s content. Even when such views are partially transparent, they still occlude the content that is underneath them.

## StackView

Stack views let you leverage the power of Auto Layout, creating user interfaces that can dynamically adapt to the device’s orientation, screen size, and any changes in the available space. The stack view manages the layout of all the views in its arrangedSubviews property. These views are arranged along the stack view’s axis, based on their order in the arrangedSubviews array. The exact layout varies depending on the stack view’s axis, distribution, alignment, spacing, and other properties.
