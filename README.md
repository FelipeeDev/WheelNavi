#Documentaion of *wheelNavi.js*
* * *

### Index
1. Introduction
2. Requirements
3. Basic usage
4. Global configuration
5. Layer configuration
6. Events
7. Licence

* * *
## 1. INTRODUCTION
*wheelNavi.js* is a jQuery plugin that is alternative for typical navigation on web projects. To start using *wheelNavi* add
``<script src="path_to_wheelnavi/wheelnavi.js"></script>`` to your `<head>` section. It also includes pack of mapped [*fontAwesome* icons](http://fortawesome.github.io/Font-Awesome/icons/).
You will see later on how to use it.

* * * 
## 2. REQUIREMENTS
*wheel Navi* required to work specific versions of technologies that are listed below:

* HTML 5
* CSS 3
* jQuery 1.9 (unless)

* * *
## 3. BASIC USAGE
Implement wheelNavi in the project is very easy. In the fastest way - You don't have to write in JS nothing. Just define your `<ul>` list by adding  `data-wheel-navi="example-wheel"` property. After that just add `<li>` list's elements. When your list is ready you'll need to put some link to handle click action and add `data-wheel-navi-target="example-wheel"`. That's all - You can try now!
But wait... you see blank elements. Don't worry. We can use fontAwsome icons in every list element. Just simply add `data-icon` property for example "twitter" and "facebook" on the other. Sounds nice? Let it work and see what's happend! But there is more: you can even make nested wheels - exactly like defining a nested lists.
See the whole example below:

    <ul data-wheel-navi="example-wheel">
         <li data-icon="facebook"><a href="http://www.facebook.com">Facebook</a></li>
         <li data-icon="twitter"><a href="http://www.twitter.com">Twitter</a></li>
         <li data-icon="camera" data-label="Nested wheel">
             <ul>
                   ...
             </ul>
         </li>
         <li data-icon="bell">Bell without link element</li>
         <li>Blank element</li>
    </ul>

Note that while defining nested wheel You should add `data-label` attribute to the `<li>` tag which keeps nested list.

* * *
## 4. GLOBAL CONFIGURATION

The alternative to using `data-wheel-navi="example-wheel"` is defining the `<ul>` element with - for example id attribute ` id="exampleWheel"` and add a js definition.
You can define default wheel configuration for all wheel on specified webpage. To do this specify following settings using *wheelNav* plugin:

    $('#exampleWheel').wheelNavi({
        size         : 'medium',
        radius       : 75,
        position     : 'absolute',
        color        : '#ffffff',
        fontColor    : '#000000',
        gradient     : false,
        contours     : true,
        icon         : null,
        showAction   : 'click',
        closeAction  : 'onClickOutside',
        maxPageLayersCount : 7,
        hintPosition : 'below',
        labels       : {
            previous : 'previous',
            next     : 'next',
            close    : 'close'
        }
    });

This are the default settings, here are what they mean:

*    size - is a predefined size of radius that You can choose from ['small', 'medium', 'large', 'x-large'].
*    radius - You can specify radius (in pixels). If You don't specify this property - will be overwritten with value of size property.
*    position - here You can choose the container position (the display property). WARNING! It's highly recommended to leave it 'absolute'.
*    color and fontColor - default colours for background and font.
*    gradient - whether arc layer should have a gradient in background.
*    contours - whether arc layer should have a contours by default.
*    icon - the default icon for all arc layers.
*    showAction - the action that will trigger wheel. By default is 'click', can be also 'onMouseMove'.
*    closeAction - determines when the wheel should by closed. 'onClickOutside' means that the wheel will be hidden when you click outside of it. Can be also 'onMouseOut' - it means that wheel will be hidden as soon as cursor went out from it.
*    maxPageLayersCount - it the number of the arcs which wheel can handle on one page at once. WARNING! It is recommended to not to setting it more then 9 because the icon size can be too small. If you put more `<li>` elements - they will be paginated.
*    hintPosition - defining the position of the hint with label. Can be set to: 'above', 'below' or 'fixedToTop'.
*    labels - here you can set a default labels for in-wheel navigation (pagination and reversing).

All these configs You can override in `<ul>` tag by using data attributes.

* * *
## 5. LAYER CONFIGURATION

You can define the specified properties for each of the `<li>` (in that case all `<li>` elements are equal to arc layer) as in example bellow:

    options : {
        3 : {
            color     : '#ffffff',
            fontColor : '#000000',
            gradient  : false,
            icon      : 'fa-cog',
            click     : function() {}
       }
    }

In this case the index value is a index of a element in the list. So you can override the color, fontColor, gradient, icon of the background of each arc layer. Here is also option to set an extra action callback on click event.

These configs can be overwritten in `<li>` tag with the data attributes like this:

    <li data-color="#ffffff" data-font-color="#000000" data-gradient="false" data-icon="fa-cog">

* * *
## 6. EVENTS

Basicly all arc layers have few actions that can be triggered. Here's small example of all possible callback/action if we have such a element:

    <li><a href="http://www.google.com">Click !</a><li>

*wheelNavi* will start `.click()` functions which is set on `<li>` and `<a>` elements. If you remember there is also possibility to define an extra click action while defining option configuration in *wheelNavi*. After all if the `href` attribute is set then it will be triggered.

* * *
## 7. LICENSE

The MIT License (MIT)

Copyright &copy; 2014 Filip Koblański

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
