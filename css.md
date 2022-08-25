# CSS Notes



# The basics



## Syntax

### Ruleset

```css
  p {
    color: blue;
  }
```
* `p` - selector
  * used to target the element(s) that will be selected
* `{ color: blue; }` - declaration block
* `color: blue` - declaration
* `color` - property
  * characteristic of the element to be modified
* `blue` - value



### Inline style

```html
<p style='color: blue;'>
  Hello, world!
</p>
```

* `<p style='color: blue;'>` - opening tag
* `style='color: blue;'` - attribute
* `color: blue;` - declaration
* `color` - property
* `blue` - value





## Stylesheets

### Internal stylesheets

* HTML files may contain a stylesheet in the `<head>` inside `<style>` tags

### External stylesheets

* May be included in HTML files with a link tag:

  ```html
  <link href='./assets/css/styles.css' rel='stylesheet'>
  ```

  * `<link>` is a self-closing tag
  * `href` - path to, or address of, the file
  * `rel` - short for relationship; how is the linked file related to this HTML file?





# Selectors

* ...decide which HTML element(s) a style applies to
* There are different kinds of selectors...



## Types of selectors

### Type

* a.k.a. **tag name selector, element selector**

* matches a particular type of element

  * e.g. `<div>` or `<h1>`

    ```css
    div {
      background-color: pink;
    }
    ```



### Universal

* selects **all** elements of **any** type

  ```css
  * {
    color: white;
    background-color: black;
  }
  ```

* Use cases: 

  * resetting default browser styling
  * **matching all children of a parent element**



### Class

* is a common way to select multiple elements of different types

* class is an attribute that an HTML element may have

  * the value of the attribute is the particular class(es) assigned to the element

* a period is used before the class name to signify that a class is being selected:

  ```css
  .contrast {
    color: cyan;
    font-family: 'Verdana';
  }
  ```

* A class is an *attribute* an HTML element may have

#### Multiple classes

* An HTML element may have multiple classes

  ```html
  <h1 class='serif bold uppercase blue'>
    Hello, world!
  </h1>
  ```

* Class names are separated by a **space**

* A class is an *attribute* an HTML element may have



### ID

* IDs are useful for selecting **a single element**

* An ID selector begins with a `#` hash

  ```html
  <h1 id='large-title'>
    Fifteen minutes could save you fifteen minutes or more...
  </h1>
  ```

  ```css
  #large-title {
    font-weight: bold;
    font-size: 2em;
  }
  ```

* An ID is an *attribute* an HTML element may have



### Attribute

* HTML elements with some particular attribute may also be selected

  ```css
  [href] {
    text-decoration: bold;
    color: cyan;
  }
  ```

  

* The attribute name is wrapped in `[` `]` brackets

* We may even select elements of a particular type, with some type of attribute that is set to some specific value:

  ```css
  img[src='./assets/images/hero.jpg'] {
    width: vw;
  }
  ```

* We can go further, by using a wildcard to select `img` elements with a `src` attribute set to some value *containing* `hero`:

  ```css
  img[src*='hero'] {
    width: vw;
  }
  ```

* The attribute selector is powerful, in that it allows us to style elements without needing to add classes or IDs, simply by selecting based on some attribute



### Pseudo-class

* Elements may have psuedo-classes, which are influenced by things like:

  * user interaction
    * e.g. clicking on a button
  * site navigation
    * e.g. visited links turn purple
  * position in the document tree (DOM)

* Psuedo-classes may be attached to any selector with a `:` colon:

  ```css
  a:hover {
    text-decoration: underline;
  }
  ```



### More on Classes and IDs

* Classes are meant to be reused for many elements
* Classes are meant to be mixed (but don't have to be!)
  * All elements which need to have a certain colour, for example, may be given the same class, e.g. `class='blue'`
* IDs are meant to style *one* specific element
* ***IDs override the styles of types and classes***
* IDs should be used sparingly for elements which have some unique style
  * Do ***not*** use an ID for more than one element! That's what ***classes*** are for.



## Using selectors

### Specificity

* ...is the order by which the browser decides which styles will be applied to elements
* Best practice is to style elements while being as non-specific as possible, i.e. using the lowest degree of specificity
  * IDs are the most specific selector
    * they select one particular element
  * Classes are the next most specific
  * Type selectors are the least specific of these three
* So, if possible, use a type selector
  * If that's not practical, use a class
    * If that's not practical either, then an ID selector may be the best option
* The most specific selector takes precedence
  * If an element is styled by type and class, the style applied to the class will override the style applied to the type
    * and, of course, ID takes precedence over class

#### Example

* HTML

  ```html
  <html>
    <head>
      <link href='specific.css' rel='stylesheet'>
    </head>
    <body>
      <a href="https://www.gnu.org" class="blue" id="gnu-link">Try something GNU!</a>
    </body>
  </html>
  ```

* CSS

  ```css
  * {
    background-color: cornflowerblue;
    color: white;
  }
  
  a {
    color: pink;
  }
  
  .blue {
    color: lightblue;
   }
  
  [href] {
    color: lightgreen;
  }
  
  [href*='gnu'] {
    color: orange;
  }
  ```

  * The order in which these styles appear in this stylesheet does not matter; the order could be inverted, and everything would behave the same.
    * The link will be orange because that is the most specific of the four selectors
    * If all selectors were equally specific, then the last one would take precedence



### Chaining

* ...is used to combine multiple selectors to select elements which are common to all the combined selectors (like a logical AND)

  ```css
  h2.info-box {
    text-decoration: underline;
  }
  ```



### Descendant combinator

* ...is used to select elements which are a descendant of other elements

  * nested inside other elements
  * this bullet, and the one above it, are descendants of the one before them
* for example:

  ```css
  .list-1 li {
    text-decoration: underline;
  }
  ```

  

  * this would select all `<li>` elements which are anywhere inside `.list-1`



### Multiple selectors

* The same style may be applied to two or more different selectors without repeating declarations unnecessarily

  * This is done with a `,` comma:

    ```css
    h1, .menu {
      font-family: Helvetica;
    }
    ```

  * The above is equivalent to:

    ```css
    h1 {
      font-family: Helvetica;
    }
    
    .menu {
      font-family: Helvetica;
    }
    ```





# Visual rules

## Font family

* The `font-family` property may be used to set the typeface of text:

  ```css
  .content {
    font-family: 'Courier New';
  }
  ```

* Font names which contain spaces should be enclosed in quotation marks
* Fonts must be embedded within your website if they are not installed on the user's computer



## Font size

* ...may be set like so:

  ```css
  p {
    font-size: 15px;
  }
  ```

  

## Font weight

* ...may be set like so:

  ```css
  h1, h2 {
    font-weight: bold;
  }
  ```

  

## Text alignment

* ...may be set like so:

  ```css
  h1 {
    text-align: center;
  }
  ```

  

## Colors

* ...may be set like so:

  ```css
  .content {
    color: white;
    background-color: midnightblue;
  }
  ```

* for a list of named colors built into CSS, see:

  https://developer.mozilla.org/en-US/docs/Web/CSS/named-color

  * the `transparent` color is an alias to `rgba(0,0,0,0)`

### Opacity

* ...is a measure of transparency
  * opacity is actually the inverse of transparency, so...
  * 100% opacity represents something that is completely opaque
    * CSS uses decimal values for opacity, so that would be a value of `1`
  * 0% opacity represents something that is completely transparent
    * In decimal, zero is still `0`



## Background

* There are several `background` properties in CSS...

  https://developer.mozilla.org/en-US/docs/Web/CSS/background

* ...one of which is:

### Background image

* ...may be set like so:

  ```css
  .hero {
    background-image: url('assets/images/hero.jpg');
  }
  ```

#### URL Constructor

* the **URL constructor** may contain a relative path for local files, or the address of some remote file

  https://developer.mozilla.org/en-US/docs/Web/API/URL/URL



## `!important`

* the `!important` flag ( which consists of a `!` delimiter followed by the `important` keyboard) causes a declaration to override any other styles, no matter how specific those other styles may be

* use it like so:

  ```css
  h1 {
    color: white !important;
  }
  ```

* one common use case is working with multiple stylesheets

  * we may be using some CSS framework, which provides many nice styles, but we wish to override some of those on our website, or on specific pages, etc.



# The box model

* every element on a webpage, no matter its shape, has a box around it
  * these boxes are used to position and style elements
* boxes have several 'parts':
  * the **content** area
    * ...which has a **width** and **height**
  * the **padding**
  * the **border**
  * the **margin**



## Width and height

* ...are pretty self-explanatory



## Borders

* may be styled using several properties, including:

  * `width`: the border's thickness
  * `style`: e.g. `solid`, `dashed`...
  * `color`

* may be styled like so:

  ```css
  p {
    border: 3px solid blue;
  }
  ```

  

* the default border values for all elements, if none are specified in a stylesheet, are `medium none color`, where `color` is the element's color

### Border radius

* gives the corners of a border the same curvature that a circle of the specified radius would have

* to create a perfect circular border:

  * make the element square, by setting its width and height to be the same

    https://spin.atomicobject.com/2015/07/14/css-responsive-square/

  * then set the `border-radius` to 50% (half the element's width)



## Padding

* ...is the space between a box's contents and its borders
* ...