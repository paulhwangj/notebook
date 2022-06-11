# React

> [Scrimba React Course](https://scrimba.com/learn/learnreact)  
> [React Installation without Manual Configuration](https://www.youtube.com/watch?v=iiHVKTZiuuw)  
> [Manual Installation of React](https://medium.com/@vikasharry03/react-setup-on-local-computer-912f9a551af3)  
> [ReactDOM render() and other functions that are now considered “legacy” after React 18](https://reactjs.org/docs/react-dom.html)
> 

---

- Table of Contents

# What we’ll learn

- Why we care about React
- JSX ⇒ proprietary React syntax
- Custom components
- CSS Styling

# Setting up React in our projects

> File Path: `/Users/paul/Documents/Personal Projects/learning_react_scrimba`
>  
 
- [Add React to a Website](https://reactjs.org/docs/add-react-to-a-website.html)
- [React Documentation to write React code in your project](https://reactjs.org/docs/cdn-links.html)
    - (Easier Method) Simple as copying the two script tags listed on the link
    - Also want to include [babel](https://reactjs.org/docs/add-react-to-a-website.html#quickly-try-jsx)
        - And add `<script src=”index.js” type=”text/babel”></script>`
- We now have access to `ReactDom`
    
    ```jsx
    ReactDOM.render(<h1>Hello, everyone!</h1>, document.getElementById("root"))
    
    second arg => places the first argument there
    ```
    
    - ReactDOM has a method `render(a, b)` allows for us to place elements on the screen.
        - a ⇒ html code
        - b ⇒ DOM Node via a statement like document.getElement…() or document.querySelector()

# Why React?

## It’s composable

- Allows us to write composable code.
    - Composable code ⇒ Taking smaller components to create something larger.
- Modern Frameworks with React ⇒ allows us to make custom components
    - This makes our code maintainable and shorter.
        - Navbar Code
            
            ```jsx
            function Navbar() {
                return (
                    <nav className="navbar navbar-expand-lg navbar-light bg-light">
                        <a className="navbar-brand" href="#">Navbar</a>
                        <button className="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                            <span className="navbar-toggler-icon"></span>
                        </button>
            
                        <div className="collapse navbar-collapse" id="navbarSupportedContent">
                            <ul className="navbar-nav mr-auto">
                            <li className="nav-item active">
                                <a className="nav-link" href="#">Home <span className="sr-only">(current)</span></a>
                            </li>
                            <li className="nav-item">
                                <a className="nav-link" href="#">Link</a>
                            </li>
                            <li className="nav-item dropdown">
                                <a className="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                                Dropdown
                                </a>
                                <div className="dropdown-menu" aria-labelledby="navbarDropdown">
                                <a className="dropdown-item" href="#">Action</a>
                                <a className="dropdown-item" href="#">Another action</a>
                                <div className="dropdown-divider"></div>
                                <a className="dropdown-item" href="#">Something else here</a>
                                </div>
                            </li>
                            <li className="nav-item">
                                <a className="nav-link disabled" href="#">Disabled</a>
                            </li>
                            </ul>
                            <form className="form-inline my-2 my-lg-0">
                                <input className="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" />
                                <button className="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
                            </form>
                        </div>
                    </nav>
                )
            }
            
            ReactDOM.render(
                <Navbar />,
                document.getElementById("root")
            )
            ```
            
        - Essentially, we are able to write HTML code and have it be returned by a function in which a function call is all that’s needed to have it render to the page.

## It’s declarative

- Declarative vs Imperative
    - Declarative ⇒ tell the program what to be done
        - The computer focuses on how its done, we don’t worry about it
    - Imperative ⇒ we have to write how a computer will do something
        - The computer asks us for directions on how to accomplish something
- Coding Challenge: Issues with Imperative Writing
    
    ```jsx
    // ReactDOM.render(<h1>Hello, React!</h1>, document.getElementById("root"))
    
    /* 
    Challenge - recreate the above line of code in vanilla JS by creating and
    appending an h1 to our div#root (without using innerHTML).
    
    - Create a new h1 element
    - Give it some textContent
    - Give it a class name of "header"
    - append it as a child of the div#root
        
    */
    const h1 = document.createElement('h1')
    h1.textContent = "This is an imperative way to program"
    h1.className = "header"
    document.getElementById('root').append(h1)
    ```
    
    - The issue with the **imperative way (above)** is that it will become **very lengthy.**
    - `ReactDOM.render(<h1 className="header">Hello, React!</h1>, document.getElementById("root"))` is a much cleaner and easier way to write the same thing.

# What is JSX?

- Think of it **as a flavor of Javascript that looks like HTML**
    - Made React **more declarative than imperative**
        
        ```jsx
        ReactDOM.render(<h1>This is JSX</h1>, document.getElementById('root'));
        ```
        
    - There are small differences (i.e: class=”xxx" ⇒ **className=”xxx”**)

## See the Difference Between JSX and Regular DOM Elements

```jsx
const h1 = document.createElement("h1")
h1.textContent = "Hello world"
h1.className = "header"
console.log(h1)

// Regular DOM Element being console log'd
// <h1 class="header">

const element = <h1 className="header">This is JSX</h1>
console.log(element)

// JSX being console log'd
/*
{
    type: "h1", 
    key: null, 
    ref: null, 
    props: {className: "header", children: "This is JSX"}, 
    _owner: null, 
    _store: {}
}
 */
```

- **React ⇒ creating JS Objects with JSX**

## JSX Only Allows the Return of a Single Parent Element

```jsx
ReactDOM.render(
    <h1 className="header">This is JSX</h1><p>This is a paragraph</p>, 
    document.getElementById("root")
)

// Causes an error because <h1> and <p> are sibling elements
// They would need to be wrapped by a parent element (see below)

ReactDOM.render(
		<div>
		    <h1 className="header">This is JSX</h1>
				<p>This is a paragraph</p>, 
		</div>
, document.getElementById("root"))
```

## We can assign a variable with any sort of JSX code

```jsx
const page = (
    <div>
        <h1 className="header">This is JSX</h1>
        <p>This is a paragraph</p>
    </div>
)

ReactDOM.render(
    page,
    document.getElementById("root")
)

console.log(page);
/*
›
{type: "div"
    , key: null
    , ref: null
    , props:
            {
                children:
					        [
                  {
                    type: "h1"
					          , key: null
	                  , ref: null
                    , props:
                        {className: "header"
                           , children: "This is JSX"}
                    , _owner: null
                    , _store: {}
                  },
                  {
                    type: "p"
                    , key: null
                    , ref: null
                    , props:
                        {
                            children: "This is a paragraph"
                         }
                    , _owner: null
                    , _store: {}
                  }
                  ]
            }
    , _owner: null
    , _store: {}
}
*/
```

- Notice that we are still able to use that element as the first argument for `render()`

## Challenge: Create a Navbar in JSX

```jsx
/* 
Challenge: 

Create a navbar in JSX:
    - Use the semantic `nav` element as the parent wrapper
    - Have an h1 element with the brand name of your "website"
    - Insert an unordered list for the other nav elements
        - Inside the `ul`, have three `li`s for "Pricing",
        "About", and "Contact"
    - Don't worry about styling yet - it'll just be plain-looking HTML for now
*/
const navbar = (
    <nav>
        <h1>Paul Hwang</h1>
        <ul>
            <li>Pricing</li>
            <li>About</li>
            <li>Contact</li>
        </ul>
    </nav>
)
ReactDOM.render(
    navbar,
    document.getElementById('root')
);
```

# Setting up React the “Correct” Way

> [React Native Environment Setup for MacOS](https://www.youtube.com/watch?v=MJEcookWYUI)
> 

# Challenge: Use .append() instead of ReactDOM.render(), what happens?

```jsx
/**
Challenge: find out what happens if we try to append JSX
to our div#root using .append() instead of ReactDOM

1. Create a sample page in JSX (≥ 4 elements) and save them in a variable
2. Select the div with the ID of "root" and use `.append()` to append
   your JSX
3. See if you can guess what will show up in the browser before running
   the code
4. See if you can explain what actually shows up in the browser
 */

const page = (
    <div>
        <h1>Paul's Life</h1>
        <h2>Education</h2>
        <p>UWO</p>
        <h2>Major</h2>
        <p>Computer Science</p>
    </div>
)
// appending the created JSX var into the div#root
document.getElementById('root').append(page)

// we can show the js object with JSON.stringify(page)
document.getElementById("root").append(JSON.stringify(page))
```

# ReactDOM’s Render Function

- This doesn’t occur with `ReactDOM` because the the `render()` function takes in JS objects / React elements and creates real html elements.

# Challenge: Fix the above challenge’s code to work (now using React Dependencies instead of just including scripts in our html)

Reference Section [“Thought Experiment: use .append() instead of ReactDOM.render()”](https://scrimba.com/scrim/co5c54662bb669f19d26693f9)

```jsx
import React from "react"
import ReactDOM from "react-dom"

const page = (
    <div>
        <h1>Paul's Life</h1>
        <h2>Education</h2>
        <p>UWO</p>
        <h2>Major</h2>
        <p>Computer Science</p>
    </div>
)

ReactDOM.render(page, document.getElementbyId('root'));
```

# Project Part 1: Mark Up

Reference Section [“Project Part 1 - Mark up”](https://scrimba.com/learn/learnreact/project-part-1-markup-coc7e4be18a0fe000d0e29e32)

## Challenge: Recreating the Google Slide

- Code
    
    ```jsx
    /*
    Challenge: Starting from scratch, build and render the 
    HTML for our section project. Check the Google slide for 
    what you're trying to build.
    
    We'll be adding styling to it later.
    
    Hints:
    * The React logo is a file in the project tree, so you can
      access it by using `src="./react-logo.png" in your image
      element
    * You can also set the `width` attribute of the image element
      just like in HTML. In the slide, I have it set to 40px
    * Note: This won't work without having the react dependencies
            included which this project does not (done on scrimba)
     */
    
    import React from "react"
    import ReactDOM from "react-dom"
    
    const slide = (
        <div>
            <img src="./react-logo.png" width="40px"></img>
            <h1>Fun Facts about React</h1>
            <ul>
                <li>Was first released in 2013</li>
                <li>Was originally created by Jordan Walke</li>
                <li>Has well over 100K stars on Github</li>
                <li>Is maintained by Facebook</li>
                <li>Powers thousands of enterprise apps, including mobile apps</li>
            </ul>
        </div>
    )
    
    ReactDOM.render(slide, document.getElementById('root'))
    ```
    

# Pop Quiz: Everything before this point!

```markdown
**1. Why do we need to `import React from "react"` in our files?**
The JSX syntax is defined in React => meaning that React needs to be a part of our code base
to allow for JSX code

**2. If I were to console.log(page) in index.js, what would show up?**
[Object] because all a JSX variable is is a JS object.

A Javascript object. React elements that describe what React should eventually add
to the real DOM for us.

**3. What's wrong with this code:**

const page = (
    <h1>Hello</h1>
    <p>This is my website!</p>
)

The problem with the above is that there is no parent element and JSX variables require
that there be a parent element.

**4. What does it mean for something to be "declarative" instead of "imperative"?**
Declarative => all we do is instruct a computer to do something with no thought on how it
						   does it.

Imperative => we tell a computer HOW to accomplish a task.

**5. What does it mean for something to be "composable"?**
It means that it's built using MANY little parts rather than starting with ONE large part.

In terms of web dev, we take pieces of the UI and break them into smaller pieces and then
combine them together to make the whole UI (reference [here](https://www.notion.so/React-eccec4325dc8484e8c2d139fb7a9426b))
```

# Custom Components

- Concept of a function ⇒ write code to run over and over again just by calling a function
    - This is what’s being done here! We want to render a navbar? Call the `NavBar()` function!
        
        ```jsx
        ReactDOM.render(<TempFunc />, document.getElementById("root"))
        ```
        

## Function and Class Components

> [React Js Documentation: Components and Props](https://reactjs.org/docs/components-and-props.html)
> 
- The information that’s under this toggle slightly differs from the process described in the scrimba course.
    
    ### Defining a Component with a JS Function or ES6 Class
    
    - This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element. We call such components “function components” because they are literally JavaScript functions.
    
    ```jsx
    function Welcome(props) {
        return <h1>Hello, {props.name}</h1>;
    }
    ```
    
    - The above is equal to the below code that utilizes ES6 class
        
        ```jsx
        class Welcome extends React.Component {
            render() {
                return <h1>Hello, {this.props.name}</h1>;
            }
        }
        ```
        
    
    ### Rendering a Component
    
    - . . .

## General Syntax: React Components / Functions

- Functions in React are not camal case, so capitalize the first word and it should be formatted with `return (. . .)`

```jsx
function NavBar() {
    return (
        . . .
    )
}
```

## General Syntax: Invoking React Components / Functions

- To invoke a function, we simply put the name of the function between two “<>” and end with “/”

```jsx
ReactDOM.render(
    <NavBar />
    document.getElementById('root')
)
```

- NOTE: that we aren’t required to utilize this in a .render() function invocation.

## Challenge (Part 1): Create a page of your own using a custom Page component

```jsx
/**
Challenge: 

Part 1: Create a page of your own using a custom Page component

It should return an ordered list with the reasons why you're
excited to be learning React :)

Render your list to the page
*/

import React from "react"
import ReactDOM from "react-dom"

function Page() {
    return (
        <ol>
            <li>Needed for my job</li>
            <li>Excited to learn something new</li>
            <li>Refreshing</li>
        </ol>
    )
}

ReactDOM.render(<Page />, document.getElementById('root'))

```

## Challenge (Part 2): Adding more elements

```jsx
/**
Challenge: 

Part 2: 
- Add a `header` element with a nested `nav` element. Inside the `nav`,
  include a `img` element with the image of the React logo inside
  (src="./react-logo.png") and make sure to set the width to something
  more manageable so it doesn't take up the whole screen
- Add an `h1` with some text describing the page. (E.g. "Reasons
  I'm excited to learn React"). Place it above the ordered list.
- Add a `footer` after the list that says: 
    "© 20xx <last name here> development. All rights reserved."
 */

import React from "react"
import ReactDOM from "react-dom"

function Page() {
    return (
        <div>
            <header>
                <nav>
                    <img src="./react-logo.png" width="40px" />
                </nav>
            </header>
            <h1>Reasons I'm excited to learn React!</h1>
            <ol>
                <li>Needed for my job</li>
                <li>Excited to learn something new</li>
                <li>Refreshing</li>
            </ol>
            <footer>© 2022 Hwang development. All rights reserved.</footer>
        </div>
    )
}

ReactDOM.render(<Page />, document.getElementById('root'))
```

- But the issue here lies in the fact that **we still have a monolithic structure here ⇒ we will be fixing that soon.**

### Pop Quiz: React Components!

```markdown
**1. What is a React component?**
It is a function that returns React Elements.
What are React Elements => objects created when returning JSX code.

**2. What's wrong with this code?**
function myComponent() {
    return (
        <small>I'm tiny text!</small>
    )
}

The issue with the code above is that the function is following camal case which is not the
standard for React functions.

**3. What's wrong with this code?**
function Header() {
    return (
        <header>
            <nav>
                <img src="./react-logo.png" width="40px" />
            </nav>
        </header>
    )
}

ReactDOM.render(Header(), document.getElementById("root"))

The issue with the above code is that the react component invocation is done improperly.
It should be:
~~Header()~~ => <Header />
```

## Composing Components

### Parent/Child Components

- Mini Challenge: Abstract out the header section of the below code into its own component.
    
    ```jsx
    import React from "react"
    import ReactDOM from "react-dom"
    
    /**
    Mini Challenge:
    Move the `header` element from Page into 
    its own component called "Header"
    */
    
    function Page() {
        return (
            <div>
                <header>
                    <nav>
                        <img src="./react-logo.png" width="40px" />
                    </nav>
                </header>
                <h1>Reasons I'm excited to learn React</h1>
                <ol>
                    <li>It's a popular library, so I'll be 
                    able to fit in with the cool kids!</li>
                    <li>I'm more likely to get a job as a developer
                    if I know React</li>
                </ol>
                <footer>
                    <small>© 2021 Ziroll development. All rights reserved.</small>
                </footer>
            </div>
        )
    }
    //=================================================================================
    ANSWER BELOW:
    
    function Header() {
        return (
            <header>
                <nav>
                    <img src="./react-logo.png" width="40px" />
                </nav>
            </header>
        )
    }
    
    function Page() {
        return (
            <div>
                <h1>Reasons I'm excited to learn React</h1>
                <ol>
                    <li>It's a popular library, so I'll be 
                    able to fit in with the cool kids!</li>
                    <li>I'm more likely to get a job as a developer
                    if I know React</li>
                </ol>
                <footer>
                    <small>© 2021 Ziroll development. All rights reserved.</small>
                </footer>
            </div>
        )
    }
    ```
    
- **In order to compose multiple components, we can invoke components inside other components**
    
    ```jsx
    function Header() {
        return (
            <header>
                <nav>
                    <img src="./react-logo.png" width="40px" />
                </nav>
            </header>
        )
    }
    
    function Page() {
        return (
            <div>
    						**<Header />  (notice the invocation here)**
                <h1>Reasons I'm excited to learn React</h1>
                <ol>
                    <li>It's a popular library, so I'll be 
                    able to fit in with the cool kids!</li>
                    <li>I'm more likely to get a job as a developer
                    if I know React</li>
                </ol>
                <footer>
                    <small>© 2021 Ziroll development. All rights reserved.</small>
                </footer>
            </div>
        )
    }
    ```
    
- Mini Challenge: Abstract out the <ol> as its own component and the footer as its own component
    
    ```jsx
    import React from "react"
    import ReactDOM from "react-dom"
    
    /**
    Challenge: 
    
    - Move the `footer` into its own component called "Footer" 
      and render that component inside the Page component.
    - Move the `h1` and `ol` together into another component
      called "MainContent" and render inside Page as well.
    */
    
    function Header() {
        return (
            <header>
                <nav>
                    <img src="./react-logo.png" width="40px" />
                </nav>
            </header>
        )
    }
    
    function MainContent() {
        return (
            <>  **(notice the use of fragments here)**
                <h1>Reasons I'm excited to learn React</h1>
                <ol>
                    <li>It's a popular library, so I'll be 
                    able to fit in with the cool kids!</li>
                    <li>I'm more likely to get a job as a developer
                    if I know React</li>
                </ol>
            </>
        )
    }
    
    function Footer() {
        return (
            <footer>
                <small>© 2021 Hwang development. All rights reserved.</small>
            </footer>
        )
    }
    
    function Page() {
        return (
            <div>
                <Header />
                <MainContent />
                <Footer />
            </div>
        )
    }
    
    ReactDOM.render(<Page />, document.getElementById("root"))
    ```
    
    - Here, the `Page()` is the parent component and the `Header(), MainContent(), Footer()` are child components (which these child components can also have child components, allowing for unlimited number of nesting).
