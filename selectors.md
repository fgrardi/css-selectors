# Selectors cheatsheet

## Basic selectors
1. `*`
- Targets every single element on the page (don't use it in production code)
- Can be used with child elements but try to avoid it

``` CSS
* {
 margin: 0;
 padding: 0;
}
```


2. `#id`
- Target by id
- Target single element
- Ask yourself: do I absolutely need to apply an id to target it?

``` CSS
#container {
   width: 960px;
   margin: auto;
}
```


3. `.class`
- Target multiple elements
- When you want to apply it to a group of elements

``` CSS
.error { /* target all elements with class error */
    color: red;
}
p.error { /* target all paragraphs with class error */
    color: blue;
}
```


4. `x`
- Element selector
- Targets all elements according to their type

``` CSS
a { color: red; }
ul { margin-left: 0; }
```

**Group** -- selects all `h1`, `h2` and `h3` elements on the page

``` CSS
h1, h2, h3 {
    foo: bar;
}
```


## Contextual selectors

5. `x y`
**Descendant** -- selects all `p` elements within the infinite-level hierarchy of element `#foo` descendants
- When you need to be more specific with your selectors

``` CSS
#foo p {
    bar: fum;
}
```

6. `x + y`
**Adjacent sibling** -- selects the sibling element `p` that is immediately next to `h2` element

``` CSS
h2 + p {
    foo: bar;
}
```

7. `x > y`
**Child** -- selects all `p` elements that are immediate children of `#foo` element
- Similar to `x y`
- Only selects direct children
- When working with JavaScript-based CSS selector engines

``` CSS
#foo > p {
    bar: fum;
}
```

8. `x ~ y`
**General sibling** -- selects all elements `p` that are siblings to the `h2` element
- Similar to `x + y` but less strict

``` CSS
h2 ~ p {
    foo: bar;
}
```


## Pseudo-class selectors
### Pseudo-class selectors for link and user states

9. **Unvisited link** 
We use the :link pseudo-class to target all anchor tags which have yet to be clicked on.

``` CSS
a:link {
    foo: bar;
}
```

10. **Visited link** -- applies to link elements that have been visited

``` CSS
a:visited {
    foo: bar;
}
```

11. **Focus state** -- applies to selected `.foo` element that is ready for input 

``` CSS
.foo:focus {
    bar: fum;
}
```

12. **Focus within state** -- applies to selected `.foo` element that is focused or has any focused child

``` CSS
.foo:focus-within {
    bar: fum;
}
```

13. **Hover state** -- applies when mouse pointer is over the `.foo` element

``` CSS
.foo:hover {
    bar: fum;
}
```

14. **Active state** -- applies when `.foo` element is in process of being clicked

``` CSS
.foo:active {
    bar: fum;
}
```

15. **Checked state** -- targets an ui element that has been checked--like a radio button

``` CSS
input[type=radio]:checked {
    border: 1px solid black;
}
```

16. **Before and after** -- generate content arount selected element
- When `overflow: hidden;` isn't possible

``` CSS
.clearfix:after {
    ...
}
```

17. **Negation** -- select everything except for one element

``` CSS
*:not(p) {
    color: green;
}
```

### Pseudo-class selectors that apply to siblings

18. **First child** -- selects the specified `.foo` element when it is the first child of its parent

``` CSS
.foo:first-child {
    bar: fum;
}
```

19. **Last child** -- selects the specified `.foo` element when it is the last child of its parent

``` CSS
.foo:last-child {
    bar: fum;
}
```

20. **Only child** -- selects the specified `.foo` element when it is the only child of its parent

``` CSS
.foo:only-child {
    bar: fum;
}
```

21. **First of type** -- selects the `h2` element when it is the first element of its type within its parent element

``` CSS
h2:first-of-type {
    foo: bar;
}
```

22. **Last of type** -- selects the `h2` element when it is the last element of its type within its parent element

``` CSS
h2:last-of-type {
    foo: bar;
}
```

23. **Only of type** -- selects the `h2` element when it is the only element of its type within its parent element

``` CSS
h2:only-of-type {
    foo: bar;
}
```

24. **Nth child** -- selects the `n`th `.foo` child element

``` CSS
.foo:nth-child(n) {
    bar: fum;
}
```

25. **Nth last child** -- selects the `n`th `.foo` child element counting backwards

``` CSS
.foo:nth-last-child(n) {
    bar: fum;
}
```

26. **Nth of type** -- selects the `n`th `h2` child element of its type

``` CSS
h2:nth-of-type(n) {
    foo: bar;
}
```

27. **Nth last of type** -- selects the `n`th `h2` child element of its type counting backwards

``` CSS
h2:nth-last-of-type(n) {
    foo: bar;
}
```

Useful `n` values:
- `odd` or `2n+1` -- every odd child or element
- `even` or `2n` -- every even child or element
- `n` -- every nth child or element
- `3n` -- every third child or element (3, 6, 9, ...)
- `3n+1` -- every third child or element starting with `1` (1, 4, 7, ...)
- `n+6` -- all but first five children or elements (6, 7, 8, ...)
- `-n+5` -- only first five children or elements (1, 2, ..., 5)


### Pseudo-element selectors
We can use pseudo elements (designated by ::) to style fragments of an element, such as the first line or the first letter. Keep in mind that these must be applied to block-level elements in order to take effect.


28. **First letter** -- selects the first letter of the specified `.foo` element, commonly used with `:first-child` to target first paragraph

``` CSS
.foo::first-letter {
    bar: fum;
}
```

29. **First line** -- selects the first line of the specified `.foo` element, commonly used with `:first-child` to target first paragraph

``` CSS
.foo::first-line {
    bar: fum;
}
```

30. **Before** -- adds generated content before the `.foo` element when used with `content` property

``` CSS
.foo::before {
    bar: fum;
    content: 'baz';
}
```

40. **After** -- adds generated content after the `.foo` element when used with `content` property

``` CSS
.foo::after {
    bar: fum;
    content: 'baz';
}
```


## Attribute selectors

41. **Present** -- selects `.foo` elements with `bar` attribute present, regardless of its value

``` CSS
.foo[bar] {
    fum: baz;
}
```

42. **Exact** -- selects `.foo` elements where the `bar` attribute has the exact value of `fum`

``` CSS
.foo[bar="fum"] {
    baz: qux;
}
```

43. **Whitespace separated** -- selects `.foo` elements with `bar` attribute values contain specified partial value of `fum` (whitespace separated)

``` CSS
.foo[bar~="fum"] {
    baz: qux;
}
```

44. **Hyphen separated** -- selects `.foo` elements with `bar` attribute values contain specified partial value of `fum` immediately followed by hyphen (`-`) character

``` CSS
.foo[bar|="fum"] {
    baz: qux;
}
```

45. **Begins with** -- selects `.foo` elements where the `bar` attribute begins with `fum`

``` CSS
.foo[bar^="fum"] {
    baz: qux;
}
```

46. **Ends with** -- selects `.foo` elements where the `bar` attribute ends with `fum`

``` CSS
.foo[bar$="fum"] {
    baz: qux;
}
```

47. **Contains** -- selects `.foo` elements where the `bar` attribute contains string `fum` followed and preceded by any number of other characters

``` CSS
.foo[bar*="fum"] {
    baz: qux;
}
```


## Misc selectors

**Not** -- selects `.foo` elements that are NOT `.bar` elements

``` CSS
.foo:not(.bar) {
    fum: baz;
}
```

**Root** -- selects the highest level parent element in the DOM

``` CSS
:root {
    foo: bar;
}
```

**Empty** -- selects `.foo` elements that have no children or whitespace inside

``` CSS
.foo:empty {
    bar: fum;
}
```

**In-range** and **Out-of-range** -- selects `.foo` elements that have values in or out of range

``` CSS
.foo:in-range {
    bar: fum;
}
.foo:out-of-range {
    bar: fum;
}
```
