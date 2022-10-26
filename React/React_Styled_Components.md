# React Styled Components

Styled Components is a CSS-in-JS styling solution for React and React Native.

This library utilizes tagged template literals to allow us to write plain CSS that is scoped to a single component inside our JavaScript code.

It is one of the most starred libraries in the React ecosystem.

## Features/Benefits

### Critical CSS

The browser must download and parse CSS files before it can show the page.

This makes CSS a render-blocking resource.

If our CSS files are large, or there are poor network conditions, requests for CSS files can significantly increase the amount of time it takes for a page to render.

_Critical CSS_ is a technique we can use to improve our page's rendering speed by extracting the CSS for above-the-fold content and inlining said styles inside the head of the HTML document.

We can then load the remainder of the CSS asynchronously.

One downside of this technique is that it prevents the browser from caching our CSS for reuse on subsequent page loads, so we should utilize critical CSS sparingly.

The other downside is that it would be tedious to manually determine the critical CSS for a page.

Fortunately, there are tools, such as the [styled-components library](https://styled-components.com/), that can automatically do this for us.

### Generated Classnames

Unique class names are automatically generated which can help prevent bugs from mispellings or duplicated class names.

### Other Features/Benefits

**Dynamic Styling** -- Styled components make it easy to apply dynamic styles.

**Automatic Vendor Prefixing** -- Vendor prefixes are automatically applied.

## Visual Studio Code Plugin

There is a [VSCode extension](https://marketplace.visualstudio.com/items?itemName=styled-components.vscode-styled-components) that provides syntax highlighting and IntelliSense for for Styled Components.

## Additional Notes

- React Styled Components can be used in conjunction with regular CSS.

- We can pass props to our styled components.

- Inside of our styled component's stylesheet we have access to the props passed and can use them to dynamically apply styles.

* We can extend the styles of existing React components by passing them into the _styled_ function.

* We can change the type of HTML element a component will be rendered as by passing our styled component an "as" prop along with a value (with the value being the type of HTML element we want). For example:

  > <StyledButton as 'a'></StyledButton>

* We can specify pseudo classes in our styled components. Here's an example for a hover state:

```
&:hover {

}
```

- The styled components library has a _keyframes_ helper for if we need to implement animations using keyframes.

* The library also has a _createGlobalStyle_ helper for if we need to implement styles globally.

## Resources

1. [React Styled Components Playlist](https://www.youtube.com/watch?v=FSCSdAlLsYM&list=PLC3y8-rFHvwgu-G08-7ovbN9EyhF_cltM&index=2)

1. [Styled Components Docs](https://styled-components.com/docs)

1. [Critical CSS](https://web.dev/extract-critical-css/)
