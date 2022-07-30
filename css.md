# CSS Notes



# The basics

## CSS Syntax

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



## Selectors

* ...decide which HTML element(s) a style applies to
* There are different kinds of selectors...

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
  * matching all children of a parent element

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

* Class names are separated by a space

### ID

* IDs are useful for selecting a single element

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
  * Do ***not*** use an ID for more than one element! Use classes for that!

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



Example:

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

  * Even if the order of styles was to be inverted, the link would still be `orange` because that is the most *specific* selector
    * If all selectors were equally specific, then the last one would take precedence
