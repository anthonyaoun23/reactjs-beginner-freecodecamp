#Notes taken for 'Learn React for free' on Scrimba.com

##Learning Philosophy
-The easy way is the hard way
-Learn by doing
-Woodworking analogy (read books, watch hours of youtube videos, but will not become good carpenter without actually building things)

##Spaced Learning & repitition are key
-Don't binge the course
-Take frequent breaks
-Re-watch past lessons for review

##Why React?
-Virtual Dom (https://www.youtube.com/watch?v=BYbgopx44vo)
-Reusable (and clearer) Web Components
-Maintained by Facebook
-Hirable (very in demand right now)

## Notes

You should be familiar with ES6...
We will use a lot of ES6 when writing in react

in js file...
ReactDOM.render(WHAT DO I WANT TO RENDER, WHERE DO I WANT IT TO RENDER)

in html file...

<div id="root"></div> is the container that will hold whatever we build with react if ReactDOM.render(WHAT DO I WANT TO RENDER, document.getElementById("root"))

JSX is like a javascript version of HTML. Most of JSX looks almost identical to HTML

With react, a lot is happening under the hood. Everything is compiling down to plain JS.

You cannot render two adjacent JSX elements:
ReactDOM.render(<h1>Hello world!</h1><p>This is a paragraph</p>, document.getElementById("root")) does not work.
ReactDOM.render(<div><h1>Hello world!</h1><p>This is a paragraph</p></div>, document.getElementById("root")) works.

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

##Parent/Child Components
Usually, your app will consists of complex hierarchies of components that eventually lead down to JSX elements

index.js can have
ReactDOM.render(<App />m document.getElementById("root"));
of course, don't forget to import App from App.js

React components should always have a capitalized first letter

View ComponentVsElement.PNG
React elements are what boil down to html elements. React components, as mentionned, are capitalized. Elements are lowercased.

DOM is refered to as a treee where the html element is the most base root of that tree.
Here the App component is the root of the tree. It can render header, MyInfo, and a footer.

The app component usually should only have components in its return.

##Styling react components
