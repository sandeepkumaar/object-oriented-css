# Object Oriented CSS

Objective  
CSS should be
  - Easy to style to components by simply adding classes
  - Flexible to modification (rather than creating a new class)
  - Maintainable (less rework on modification)


## Principles
 - Object Orientation
 - Single Responsibility
 - Open/Closed Principle
 - DRY (Dont Repeat Yourself)
 - Separation of Concern

The above Principles boils down to these core basic design Philosophy    
> Program to an **Abstraction**, not to an implementation      
> Favour **Composition** over Inheritance

Let us see how the above two principles get applied to all other design principles !

#### Object Orientation
Break larger programs into simple, smaller, Independent Objects
that has single responsibility/role/job.  
Objects are composed to form a Larger program  




#### Single Responsibility
A CSS Class should do only one thing  

An Object should do one thing so it is easier to *compose* with other objects.



#### Open/Closed Principle
A CSS class should be open to *extension* but closed to *modification*  

*extension* through *composition* and since class is going to follow single responsibility there is less requirement to *modify* the class

#### DRY
The styles are not to be repeated in every class  
In other words, style repeatition on classes should be kept minimum, by identifying the role/responsibility of the class  

By *Abstracting* the common properties we can do code reuse

#### Separation of Concern
Classes can be grouped to address a *concern*
Eg: Layout concern, Browser default style concern, App shell concern, typography of the site etc...  
*Concerns* are placed in a separate *file*  

*Abstraction* allows a modular/pluggable architecture  

As Quoted by Nicole Sullivan who introduced OOCSS,
> Separate **Structure** and **Skin**  
> Separate **Container** and **Content**



1. Here structure means html tags and skin is the styles applied
to those tags. They should be seperated/abstracted by
not coding/styling to the tags but to classes


2. Container is the parent element holding the child elements/components. The container class/definition should not influence/modify the behaviour/style of the child components




The above two principles talks about **Abstraction**  
This essentially means separate a webpage into
  - Structure
    - Raw page contents includes paragraphs, images, buttons, all *html elements*
  - Skin
    - is the text styles, color, background, borders
  - Container
    - Layouts, How the contents are laid out on the page
  - Content   
    - components of the applications

CSS progression
  - CSS for html tags,contents
    - Reset css


  - CSS for skin
    - typography.css
    - theme.css
    - util.css
      - borders
      - atomic.css
      - commonly used handy styles

  - CSS for Container
    - layout.css

  - CSS for site specifics (components)
    - buttons
    - Cards
    - Media objects
    - other components  


  - Modules
    - Above all are grouped - Separation of concern so that they can be independently loaded/used/switched with other similar module


##### Modules can be

> Remember   
By definition of **Modular** means they can be **pluggable**.
meaning they can be replaced with some other similar module to achieve what the *replaced* module did  
> Eg: Grid Module's job is to lay out the contents of the page. Now our Grid module might use floats to achieve the behaviour, this can be replaced by another Grid module which uses flex-box. But the *behaviour* both modules offer is the same  

###### Reset.css (content)
To override the Browser styles

###### Layout.css (structure)
Different Layouts with media queries for responsiveness
Note:  
- Defines how elements are laid out  
- Should not decide contents Height  
- Can restrict contents/components width. Content by default takes  full width
- Can decide how elements are placed and spaced  

###### Utilities.css
  - borders
  - Individual style property css class/ atomic css  


Atomic css is a methodology where a class represents a css property  
Eg:  
```
.text-center {
  text-align: center;
}
.flex {
  display: flex;
}
```

Though we are coding to abstractions (text-center) of text-align property, these
are not real abstractions. we are not really abstracting anything  
Hence these classes should be used minimum.  
Yet, sometimes you need to add a specific style property to a component at runtime  or simply it is too untidy(fails single responsibility). In that case, we either  
  - use style attr and write the property to the element
  - have a css class that represents the property which follows composition

The latter is preferred.  

>Note:  
>Component *variations* can be represented thru --class   
>Having this way allows us to understand the complete behaviour of the component and
>can be reused elsewhere  



##### Components (App specific)
Contains Application specific components  
The Component classes can be *abstracted* and extended with other component classes
*composed* to represent the complete behaviour
Eg:  
```
/*Base Button Component*/

.btn {
  min-width: 160px;
  padding: 8px;
  border-radius: 6px;
}

```

>Note: Important  
Here note the border property  
Assuming that all type of buttons in the application is going to have border-radius of 6px it would be better to code them in the .btn class  
But what if in future, the requirement that some buttons will have border and some dont  
We need to write another class that *overrides* (Inheritance) the basic behaviour.This is should not be done.  

Like said, we need separate content from skin. Here border is the skin  

We have *utility* border class that can be *composed* if a button needs border.
for buttons that dont need borders dont compose them.  
```
/* base button */
.btn {
  min-width: 160px;
  padding: 8px;
}

/* border-utility */
.border-radius-6{
  border-radius: 6px;
}
```
This looks good. We can write this way throughout the application by composing them.  

Now, What if border-radius has to be changed from 6px to 4px ??!!!   
We cannot modify border-utility class as that may have used on other components that dont need to change.  
We need to *remove* the border-6 class and replace them with border-4 class.
Now, imagine we have defined throughout the application. Replacing them is a nightmare.  

Solution:  
Use the component variation class
```
.btn {
  min-width: 160px;
  padding: 8px;
}

  .btn__border{
    border: 1px solid;
  }

  .btn__border--border-radius{
    border-radius: 6px;
  }
```
If we want change the border-radius 6px to 4px simply modify the btn__border--border-radius :)

How to add border color??  
border color depends on


> Note:  
> Grid controls width  
> Content controls/defines Height  
> By default Content takes full width







Note:
Extending Objects
Class order should impact the cascade


What bootstrap offers on these spaces??


---------------------------------------
## Reset.css
### Purpose
To reset most of the **user agent styles** that are
  - *inconsistent* across different browsers
  - unnecessary/not needed for the element  

This way, unwanted, inconsistent browsers styles are reset so
we can write our own styles (Author style) which will render
effectively without unexpected behaviours

We will use meyer's css as it is
  - simple
  - Resets all elements to Zero
  - Extended to our needs/latest design taste
  - Unlike other resets (Normalize.css), its *does not include*
  the skin(fonts), content(padding) or layout(margin) properties
