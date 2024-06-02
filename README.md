# configjs
A javascript configuration library.  
You run things like `addNumber("Image width",callback,5)` and it will make an HTML number input element with a label that says "Image width: ", a callback and a value of 5.  
You can then do `setPropertyValue("Image width",7)` and `updateNumber("Image width")` and it will update the input element's value.

## Demo
```html
<body>
    <h1>hello</h1>
    <div id="config"></div>
</body>
```
```js
let coolNumber = 5;

// This will create an <input type="number"> element in the config <div>
// The callback function makes sure that the value is a valid number, and then sets coolValue to the value
addNumber("Cool number",(ev)=>{
    let value = parseFloat(ev.target.value);
    if (value != NaN) {
        coolNumber = value;
    }
},coolNumber, 0.5); // The last 2 arguments are the current value and the step size for the input element

addLineBreak();

// This makes a button with an onclick callback
addButton("Do some math",(ev)=>{
    alert(`Here's a different number: ${coolNumber*2 + 5}`);
})
```

## Features
- Variable types:
    - Numbers
    - Lists (textarea with JSON encoded lists, could possibly be used for non-list things)
    - Booleans (checkboxes)
    - Choices (Dropdown box)
- Buttons
- Non-input things:
    - Line breaks (`<br>`)
    - Seperators (`<hr>`)
    - Labels (`<p>`, probably should be called something else to avoid confusion with `<label>`)
        - Can be used to display a variable

## Plans
- Make the whole script into a class so you can have multiple config areas and to avoid variable name conflicts
- Add custom attributes to the `addXYZ()` functions
    - You could set a certain element to have a certain class
- Use identifiers for accessing properties, and have seperate "display names" be displayed (ex. `image-width` instead of `Image width`)
    - This would also let you set the identifier as the element's ID, for better accesability
- Put each property in it's own `<div>` or other container
- The ability to delete properties and their elements (becomes much easier with the last thing because you only need to delete the container)
- Add more variable types
    - Strings, colors, dates
- Put the callback argument at the end of each 
`addXYZ()` function instead of the second element
- Publish to NPM and/or some other CDN. (Using GitHub Pages is probably a bad idea)