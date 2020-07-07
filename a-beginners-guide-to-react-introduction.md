# A Beginners Guide to React Introduction

To create a user interface using just JavaScript, there must be a root element that you can append to.  
You then gain access to the root by using the DOM api, and you can then begin appending  
newly created elements to the page. In the JavaScript you would create the element, then  
begin adding classes, attributes etc. to it.

To use Reactjs, react and react-dom are required packages.

## React create element

Making a simple UI using the React api can be done in a few ways. First way to accomplish  
this is the React.createElement method. This API different from the DOM api. Instead of  
creating/retrieving the element and then adding classes to it, in React you pass the type  
of element, and define it's classes, attributes, etc, in an object as the second argument.  
EX:

```
const rootElement = document.getElementById('root')
// without React
const element = document.createElement('div')
const element.textContent = 'Hello World'
element.className = 'container'
rootElement.appendChild(element)
// with React
const element = React.createElement('div', {
  children: 'Hello World',
  className: 'container',
})
ReactDOM.render(element, rootElement)
```

That second argument, in React, is known as the element's props.  
It is also possible to pass any number of arguments after after the props object and they  
will serve as the element's children.

To create React elements and render them to the page, you need to include React and  
ReactDOM, React for creating the elements and ReactDOM for rendering those elements to  
the page. You will still need a root element to append the created children to.

### Creating a User Interface with React's JSX syntax

Creating React elements using React.createElement works fine but it's not ergonomic and not  
what most in the community are using JSX. Which is an HTML like syntax in our Javascript  
EX:

```
<script>
const element = <div className="container">Hello World</div>
</script>
```

If you put this in the browser, it would error out because the browser does not understand  
JSX natively. It doesn't understand HTML in our JavaScript code. It needs to be compiled  
into something the browser does understand.

This is where BABEL comes in, which basically enables developers to use the JavaScript of the  
future or use not standard Javascript like JSX, right now. BABEL will actually compile the  
JSX into something very familiar, the React.createElement API.

You can go to BABEL's website and see the code you write, and how it is compiled into  
something the browser can understand.

In a typical application you would use a tool that would use BABEL to compile your code  
into something the browser understands.

You can interpolate values with these curly braces by putting any expression between  
the curly braces and have that expression passed along to the React.createElement API.

In React, you can also spread the props in the props position of a JSX element and those  
props will be combined with the other props that provided to that element in a declaractive  
and deterministic way.

```
<script type="text/babel">
  const rootElement = document.getElementById('root')
  const children = 'Hello World'
  const className = 'container'
  const props = {children, className}
  const element = <div id="app/root" {...props} className="not-container" />
  ReactDOM.render(element, rootElement)
</script>

```

Last declared value for a prop will take precedence even if that prop was populated earlier  
on. This can be useful when you want to override a property after using the spread operator  
on an object to copy props to an element.

Since JSX is not HTML, it is actually possible to have self-closing tags and completely omit the closing tag.

### React - How to Render two elements side by side?

In React it is not possible to simply put two elements side by side.  
In HTML this a pretty simple task just,

```
<span>Hello</span> <span>World</span>

```

React.Fragment allows you to have multiple elements side by side
