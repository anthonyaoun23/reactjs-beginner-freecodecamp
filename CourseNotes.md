# Notes taken for 'Learn React for free' on Scrimba.com

## Learning Philosophy
-The easy way is the hard way
-Learn by doing
-Woodworking analogy (read books, watch hours of youtube videos, but will not become good carpenter without actually building things)

## Spaced Learning & repitition are key
-Don't binge the course
-Take frequent breaks
-Re-watch past lessons for review

## Why React?
-Virtual Dom (https://www.youtube.com/watch?v=BYbgopx44vo)
-Reusable (and clearer) Web Components
-Maintained by Facebook
-Hirable (very in demand right now)

## Notes
You should be familiar with ES6...
We will use a lot of ES6 when writing in react

in js file...
```
ReactDOM.render(WHAT DO I WANT TO RENDER, WHERE DO I WANT IT TO RENDER)
```
in html file...
```
<div id="root"></div> is the container that will hold whatever we build with react if ReactDOM.render(WHAT DO I WANT TO RENDER, document.getElementById("root"))
```
JSX is like a javascript version of HTML. Most of JSX looks almost identical to HTML

With react, a lot is happening under the hood. Everything is compiling down to plain JS.

You cannot render two adjacent JSX elements:
```
ReactDOM.render(<h1>Hello world!</h1><p>This is a paragraph</p>, document.getElementById("root")) does not work.
ReactDOM.render(<div><h1>Hello world!</h1><p>This is a paragraph</p></div>, document.getElementById("root")) works.
```

Adjacent JSX elements must be wrapped in an enclosing tag.

Exercise 1: Find in Exercise1.js

Exercise 2: Find in Exercise2.js

One of the main benefits of React is that we have the ability to create our own components
By convention, we should only have 1 component per file.
File should have same name as component (spelt exactly the same, for simplicity)

To export component from file, use
export default NameOfComponent

then where you want to use the component, use
import MyInfo from 'filepath/MyInfo.js'

there is no need to have .js at end of import file because it is assumed that import files are js

It is important to stay organized when building apps. Something you can always do is create a folder names Components which holds all components you create

## Parent/Child Components
Usually, your app will consists of complex hierarchies of components that eventually lead down to JSX elements

index.js can have
```
ReactDOM.render(<App />m document.getElementById("root"));
```
of course, don't forget to import App from App.js

React components should always have a capitalized first letter

View ComponentVsElement.PNG
React elements are what boil down to html elements. React components, as mentionned, are capitalized. Elements are lowercased.

DOM is refered to as a treee where the html element is the most base root of that tree.
Here the App component is the root of the tree. It can render header, MyInfo, and a footer.

The app component usually should only have components in its return.

## Mixing Javascript and JSX Together
```
const firstName = "Bob"
const lastName = "Ziroll"

return (<h1>Hello firstName + " " + lastName!</h1>)
```

> This will not work. As expected, this will interpret whatever is in the h1 tag as text. The way to get around this is to wrap any javascript that you want to be interpreted by curly braces.

> Let's take a look at the lines of code above. Everything other than the like containing the h1 tag is interpreted as JS. The line containing the h1 is interpreted as JSX and is treated just like HTML. Adding curly braces will allow you to have JS inside your JSX.

Ex:
```
function App() {
const date = new Date()
const hours = date.getHours()
let timeOfDay

if (hours < 12) {
timeOfDay = "morning"
} else if (hours >= 12 && hours < 17) {
timeOfDay = "afternoon"
} else {
timeOfDay = "night"
}

return (<h1>Good {timeOfDay}!</h1>)
}
```

## Styling react components
```
 <h1 style="color: #FF8C00">Good {timeOfDay}!</h1> //will not work.
 ```

> Invariant Violation: The `style` prop expects a mapping from style properties to values, not a string. For example, style={{marginRight: spacing + 'em'}} when using JSX. (/node_modules/fbjs/lib/invariant.js:42)
```
  <h1 style={{color: "#FF8C00"}}>Good {timeOfDay}!</h1> will solve the problem.
```

Something to remember is that when writing style inline, you cannot have a dash in js for variable names. When this occurs, you should simply use cammel case syntax instead.
```
style={{color: "#FF8C00", background-color: "#FF2D00"}} will not work
style={{color: "#FF8C00", backgroundColor: "#FF2D00"}} will work
```
This can get long, so...
```
const styles = {
color: "#FF8C00",
backgroundColor: "#FF2D00"
}

return (

<h1 style={styles}>Good {timeOfDay}!</h1>
)
```

Having a variable for styles is a nice generic way of holding all your styling in a clean way.

fontSize: "200px" is how you would have a js value for font size.

## Props - Understanding The Concept

In regular HTML, an anchor (<a>) tag is useless without an href property. You must give it an href property so that it can link to something. Similarly, an image (<img>) needs a src property and value to display an image. Without that, nothing will show and it is completely useless. An input tag is interesting because without any properties/attributes, it will display on the page, however giving attributes like placeholder, name, and type will modify it and change the way it looks on the website.

In React, we can make our components accept different properties and display differently using props.

##Components w/ Props

<div className="contact-card">
    <img src="http://placekitten.com/300/200"/>
    <h3>Mr. Whiskerson</h3>
    <p>Phone: (212) 555-1234</p>
    <p>Email: mr.whiskaz@catnap.meow</p>
</div>

Becomes 

<ContactCard 
    name="Mr. Whiskerson" 
    imgUrl="http://placekitten.com/300/200" 
    phone="(212) 555-1234" 
    email="mr.whiskaz@catnap.meow"
/>

All the different HTML tags essentially will turn into props for components. Now, here, you will access the props and their values in the ContactCard.js file.

function ContactCard(props) {
    return (
        <div className="contact-card">
            <img src={props.imgUrl}/>
            <h3>{props.name}</h3>
            <p>Phone: {props.phone}</p>
            <p>Email: {props.email}</p>
        </div>
    )
}

## Lifecycle Methods
A lot is happening in the background when you are working with React. React components go through a series of phases/milestones during its lifetime in our application. Every componenent will under go a series of events when its being rendered and updated.

http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/ is a nice visualisation of this.
https://engineering.musefind.com/react-lifecycle-methods-how-and-when-to-use-them-2111a1b692b1
https://reactjs.org/blog/2018/03/29/react-v-16-3.html#component-lifecycle-changes

1- The render method -> like getting dressed for the day. It determines what gets rendered to the screen. This method can be called many times. When react notices a change like a prop of state change, React will re-render the component.
2- ComponentDidMount -> you were just born. This method runs the very first time the component shows up on the screen. When a component is re-rendered, it is not un-mounted and re-mounted. This method is nice for doing things like making api calls 
3- ComponentWillReceiveProps -> When someone gives you a gift. The componenent can be receiving props from a parent componenent. Every time this happens, this method will run. It receives a parameter called "nextProps". It's essentially a method to check wehter or not the props have changed. That said, this method will be depracated. You should not use this. Once React 17 comes out, this method will be completely removed, but it's still good to know in case you are looking at legacy code.
4- shouldComponentUpdate -> Making a decision as to whether you should chnage your clothes or not. Behind the scene, if React has any  kind of question at all as to whether a component needs to re-render, it will always chose to re-render the componenent just in case. Re-rendering can slow down big applications if the componenent is large and componenents can be re-rendered uselessly. This method allows us to stop that from happenning, or at least add some logic as to when the componenent should re-render. It receives parameters "nextProps" and "nextState". You must return true if you want it to update. Return false if you don't.
5- componentWillUnmount -> Just like in life, all good things come to an end, and your componenent will eventually unmount/dissapear from the screen. The main use for this method is to do some cleanup or teardown of anything that you have setup that could potentially leave some clutter in the DOM or in the application. For ex: If you in componentDidMount wanted to add an eventListener, this method would be a chance to remove that. 

6- getDerivedStateFromProps is a Static method and receives "props" and "state". You return the new, updates sstate based upon the props
https://reactjs.org/docs/react-component.html#static-getderivedstatefromprops
https://reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html
7- getSnapshotBeforeUpdate -> Create a backup of the current way things are. An object called snapshot.
https://reactjs.org/docs/react-component.html#getsnapshotbeforeupdate

## Conditional Rendering
Load something on screen if a condition is true.
    // &&
    // true && false
    Js check the bool value of the thing on the left. If it is true, it immidietly return the thing on the right. When its false, it return false right away.

## Fetching Data from an API
Built in JS tool called fetch - nice, easy promised based way to perform http requeswts so we can get any kind fo data we need.
https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch

Starwars API CORS Enabled
https://swapi.co/

Promises
https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

Inside of componentDidMount, we can call fetch("https://swapi.co/").then(response => response.json()).then(data=>console.log(data))
.json() turns data into js object JSON...

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```






            
