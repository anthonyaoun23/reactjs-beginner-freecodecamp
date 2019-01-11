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

##Functional Components
