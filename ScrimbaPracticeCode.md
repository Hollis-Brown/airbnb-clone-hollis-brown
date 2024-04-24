### Vid 2
- Challenge: Build the Navbar component.
- Check the Figma file for the design specifics.
```jsx
// App.js file code
import React from "react"
import Navbar from "./components/Navbar" // Remember to import the component, voila! - life is good.

export default function App() {
    return (
        <div>
            <Navbar />
        </div>
    )
}
// Navbar.js file code
import React from "react"

export default function Navbar() {
    return (
        <nav>
            <img src="../images/airbnb-logo.png" className="nav--logo"/>
        </nav>
    )
}
// CSS styling is pretty easy to estimate, and is handily provided.
```

### Vid 3
- Challenge: Build the Hero component.
- Check the Figma file for the design specifics.
```jsx
// App.js file code
import React from "react"
import Navbar from "./components/Navbar"
import Hero from "./components/Hero"

export default function App() {
    return (
        <div>
            <Navbar />
            <Hero />
        </div>
    )
}

// Hero.js file code
import React from "react"

export default function Hero() {
    return (
        <section className="hero">
            <img src="../images/photo-grid.png" className="hero--photo" />
            <h1 className="hero--header">Stephen Grider's course is better than Bob Ziroll's course.</h1>
            <p className="hero--text">Bob's the type of guy who's voice is perennially cheery like the ever-blooming sunflowers in a field. Idk.</p>
        </section>
    )
}
```
### Vid 4
- Challenge: Build the Card component. For now, hard-code in the data (like the rating, title, price, etc.)
Notes:
- Only render 1 instance (I already did this for you)
- The star icon and photo (katie-zaferes.png) are in the images 
  folder for your use
- Make sure to include:
    - image
    - star icon (star.png), rating, and review count
    - title
    - cost/person
- The main purpose of this challenge is to show you where our limitations
  currently are, so don't worry about the fact that you're hard-coding all
  this data into the component.

```jsx
// Card.js
import React from "react"

export default function Card() {
    return (
        <div className="card">
            <img src="../images/katie-zaferes.png" className="card--image" />
            <div className="card--stats">
                <img src="../images/star.png" className="card--star" />
                <span>5.0</span>
                <span className="gray">(6) • </span>
                <span className="gray">USA</span>
            </div>
            <p>Life Lessons with Katie Zaferes</p>
            <p><span className="bold">From $136</span> / person</p>
        </div>
    )
}
```

```css
/* style.css */
.card {
    width: 175px;
    font-size: 12px;
}

.card--image {
    width: 100%;
    border-radius: 9px;
}

.card--stats {
    display: flex;
    align-items: center;
}

.card--star {
    height: 14px;
}
```
### Vid 9
- Challenge: finish off the h1 below so it says "Hello Joe Schmoe!"

```jsx
// index.js
import React from "react"
import ReactDOM from "react-dom"

function App() {
    const firstName = "Joe"
    const lastName = "Schmoe"

    return (
        
        <h1>Hello {firstName} {lastName}!</h1> // This is the answer to the challenge 
    )
}

ReactDOM.render(<App />, document.getElementById("root"))
```
- Challenge: fix the h1 below to use the `timeOfDay` string we determined in the code above.

```jsx
// index.js
import React from "react"
import ReactDOM from "react-dom"

function App() {
    const date = new Date()
    const hours = date.getHours()
    let timeOfDay
    
    if (hours < 12) {
        timeOfDay = "morning"
    } else if (hours >= 12 && hours < 13) {
        timeOfDay = "afternoon"
    } else {
        timeOfDay = "night"
    }
    
    return (
        <h1>Good {timeOfDay}!</h1> // Was previously "<h1>Good afternoon!</h1>" 
    )
}

ReactDOM.render(<App />, document.getElementById("root"))
```        
### Vid 10
- Challenge:
    - Create a Contact.js component in another file
    - Move one of the contact card `<div>` below into that file
    - import and render 4 instances of that contact card
        - Think ahead: what's the problem with doing it this way?
```jsx
// App.js
import React from "react"
import Contact from "./Contact"

function App() {
    return (
        <div className="contacts">
            <Contact />
            <Contact />
            <Contact />
            <Contact />
        </div>
    )
}
   
// Contact.js
import React from "react"

export default function Contact() {
    return (
        <div className="contact-card">
            <img src="./images/mr-whiskerson.png"/>
            <h3>Mr. Whiskerson</h3>
            <div className="info-group">
                <img src="./images/phone-icon.png" />
                <p>(212) 555-1234</p>
            </div>
            <div className="info-group">
                <img src="./images/mail-icon.png" />
                <p>mr.whiskaz@catnap.meow</p>
            </div>
        </div>
    )
}
```
### Vid 11
- Challenge: Fix the code below to use the `props` object values in place of the hardcoded values below
```jsx
// Contact.js
import React from "react"

export default function Contact(props) {

    return (
        <div className="contact-card">
            <img src={props.img}/> 
            <h3>{props.name}</h3> 
            <div className="info-group">
                <img src="./images/phone-icon.png" />
                <p>{props.phone}</p> 
            </div>
            <div className="info-group">
                <img src="./images/mail-icon.png" />
                <p>{props.email}</p> 
            </div>
        </div>
    )
}
```
### Vid 12
- Quiz
    1. What do props help us accomplish?
        - Data sharing and communication between components.



    2. How do you pass a prop into a component?
        - By adding the prop as an attribute when rendering the component, e.g., 
        ```jsx
        <ComponentName propName={propValue} />.
        ```

    3. Can I pass a custom prop (e.g. `blahblahblah={true}`) to a native
    DOM element? (e.g. <div blahblahblah={true}>) Why or why not?
        - No, custom props cannot be passed to native DOM elements. Only valid HTML attributes are allowed on native DOM elements.


    4. How do I receive props in a component?
    ```jsx
    function Navbar() {
    return (
        <header>
            ...
        </header>
        )
    }
    ```
        - Access props using the props object e.g., `props.propName`

    5. What data type is `props` when the component receives it?
        - Props is an object.
### Vid 13
- Challenge: fix the bug, now that we've destructured the props object
```jsx
// Contact.js
import React from "react"

export default function Contact(props) {
    
    return (
        <div className="contact-card">
            <img src={props.img}/>
            <h3>{props.name}</h3>
            <div className="info-group">
                <img src="./images/phone-icon.png" />
                <p>{props.phone}</p>
            </div>
            <div className="info-group">
                <img src="./images/mail-icon.png" />
                <p>{props.email}</p>
            </div>
        </div>
    )
}

```
### Vid 14
- Challenge:
<mark>One LAST time in this course, set up a React app from scratch</mark> - easy!
    - Render an <App /> component
        - App should be in its own file
    - App should render 4-5 <Joke /> components (Joke component defined in its own file too)
        - Each Joke should receive a "setup" prop and a "punchline" prop and render those however you'd like
    - Use your favorite 2-part jokes (setup & punchline), or check `jokes.md` file for some examples.

```jsx
// Challenge
// index.js
import React from "react"
import ReactDOM from "react-dom"
import App from "./App"

ReactDOM.render(<App />, document.getElementById("root"))
// App.js
import React from "react"
import Joke from "./Joke"

export default function App() {
    return (
        <div>
            <Joke 
                setup="I got my daughter a fridge for her birthday." 
                punchline="I can't wait to see her face light up when she opens it." 
            />
            <Joke 
                setup="How did the hacker escape the police?" 
                punchline="He just ransomware!" 
            />
            <Joke 
                setup="Why don't pirates travel on mountain roads?" 
                punchline="Scurvy." 
            />
            <Joke 
                setup="Why do bees stay in the hive in the winter?" 
                punchline="Swarm." 
            />
        </div>
    )
}
// Jokes.js
import React from "react"

export default function Joke(props) {
    return (
        <div>
            <h3>{props.setup}</h3>
            <p>{props.punchline}</p>
            <hr />
        </div>
    )
}

```
### Vid 15
- Challenge: Think critically - how would you pass in a prop that wasn't a string datatype.
    - E.g. Say you want each Joke component to receive an "upvotes" and "downvotes" prop that is a number, as well as a prop with an array of comments, and a boolean of whether the joke is a pun (`isPun`).
    - How I'd pass in a prop that isn't a string datatype is the boolean, which from my electronics studies showed it's just another form of an on/off switch. 

### Vid 16
- Challenge: Pass props to the Card component and display that data
    - img ("katie-zaferes.png")
    - rating ("5.0")
    - reviewCount (6)
    - country (Whatever you want)
    - title ("Life Lessons with Katie Zaferes")
    - price (136)
```jsx
// App.js
import React from "react"
import Navbar from "./components/Navbar"
import Hero from "./components/Hero"
import Card from "./components/Card"

export default function App() {
            // <Hero />
    return (
        <div>
            <Navbar />
            <Card 
                img="katie-zaferes.png"
                rating="5.0"
                reviewCount={6}
                country="USA"
                title="Life Lessons with Katie Zaferes"
                price={136}
            />
        </div>
    )
}
// Card.js
// This example messed me up because I didn't realize I could use backticks inside of the JavaScript curly braces or whatever - live and learn.
mport React from "react"

export default function Card(props) {
    console.log(props)
    return (
        <div className="card">
            <img src={`../images/${props.img}`} className="card--image" />
            <div className="card--stats">
                <img src="../images/star.png" className="card--star" />
                <span>5.0</span>
                <span className="gray">(6) • </span>
                <span className="gray">USA</span>
            </div>
            <p>Life Lessons with Katie Zaferes</p>
            <p><span className="bold">From $136</span> / person</p>
        </div>
    )
}
```
### Vid 17
- Challenge 1:
    - Given an array of numbers, return an array of each number, squared
```jsx
const nums = [1, 2, 3, 4, 5] 
// Your code here
const squares = nums.map(function(num) {
    return num * num
})

console.log(squares) // Output: [1, 4, 9, 16, 25]
```
- Challenge 2:
    - Given an array of strings, return an array where the first letter of each string is capitalized
```jsx
const names = ["alice", "bob", "charlie", "danielle"]
// Your code here
const capitalized = names.map((name) => {
    return name[0].toUpperCase() + name.slice(1)
})

console.log(capitalized) // Output: ["Alice", "Bob", "Charlie", "Danielle"]
```

- Challenge 3:
    - Given an array of strings, return an array of strings that wraps each of the original strings in an HTML-like <p></p> tag.
    - E.g. given: ["Bulbasaur", "Charmander", "Squirtle"] 
    - return: ["<p>Bulbasaur</p>", "<p>Charmander</p>", "<p>Squirtle</p>"]
```jsx
const pokemon = ["Bulbasaur", "Charmander", "Squirtle"]
// Your code here
const paragraphs = pokemon.map(mon => `<p>${mon}</p>`)

console.log(paragraphs) // Output: "[<p>Bulbasaur</p>", "<p>Charmander</p>", "<p>Squirtle</p>"]
```
### Vid 18
- Challenge: turn the strings in the array into `<h3>` elements instead
```jsx
// Wrong example
import React from "react"
import Joke from "./Joke"

export default function App() {
    const colors = [
            <h3>Red</h3>, 
            <h3>Orange</h3>, 
            <h3>Yellow</h3>,
            <h3>Green</h3>,
            <h3>Blue</h3>,
            <h3>Indigo</h3>,
            <h3>Violet</h3>
        ]
    return (
        <div>
            <h3>Red</h3>
            <h3>Orange</h3> 
            <h3>Yellow</h3>
            <h3>Green</h3>
            <h3>Blue</h3>
            <h3>Indigo</h3>
            <h3>Violet</h3>
        </div>
    )
}
      
// Right example
import React from "react"
import Joke from "./Joke"

export default function App() {
    const colors = [
            <h3>Red</h3>, 
            <h3>Orange</h3>, 
            <h3>Yellow</h3>,
            <h3>Green</h3>,
            <h3>Blue</h3>,
            <h3>Indigo</h3>,
            <h3>Violet</h3>
        ]
    return (
        // Keep simple, or DRY: don't repeat yourself - the fundamental principle of software development to reduce repetition of information and code duplication by promoting the use of abstractions and avoiding redundancy.
        <div>
            {colors} 
        </div>
    )
}
```
### Vid 19 
- Challenge: See if you can correctly pass the necessary props to the Joke component in the .map() (and render the jokeElements array) so the jokes show up on the page again
```jsx
// App.js
import React from "react"
import Joke from "./Joke"
import jokesData from "./jokesData"

export default function App() {
    const jokeElements = jokesData.map(joke => {
        return <Joke setup={joke.setup} punchline={joke.punchline} />
    })
    return (
        <div>
            {jokeElements}
        </div>
    )
}
```
### Vid 20
- Quiz
    1. What does the `.map()` array method do?
        - The .map() method iterates over an array and returns a new array with transformed elements based on a provided callback function.


    2. What do we usually use `.map()` for in React?
        - In React, we commonly use .map() to iterate over an array of data and dynamically render components for each item in the array.


    3. Why is using `.map()` better than just creating the components
    manually by typing them out?
        - Using .map() allows for dynamic and efficient rendering of components based on the data, getting rid of repetitive code and enables easier management of dynamically changing lists or arrays of data and stuff.

### Vid 22
- Challenge:
    - import the array of data from data.js
    - map over the array to create <Card /> components
    - display the array of card components under the navbar
        - (in place of the current <Card /> component)
```jsx
// Wrong
import React from "react"
import Navbar from "./components/Navbar"
import Hero from "./components/Hero"
import Card from "./components/Card"
import data from "./data"

export default function App() {
            // <Hero />
    const cards = data.map(item => {
        return (
            <Card 
                img={item.coverImg}
                rating={item.stats.rating}
                reviewCount={item.stats.reviewCount}
                location={item.location}
                title={item.title}
                price={item.price}
            />
        )
    })        
    
    return (
        <div>
            <Navbar />
            {cards}
        </div>
    )
}
// Right
import React from "react"
import Navbar from "./components/Navbar"
import Hero from "./components/Hero"
import Card from "./components/Card"
import data from "./data"

export default function App() {

    const cards = data.map(item => {
        return (
            <Card 
                img={item.coverImg}
                rating={item.stats.rating}
                reviewCount={item.stats.reviewCount}
                location={item.location}
                title={item.title}
                price={item.price}
            />
        )
    })        
    
    return (
        <div>
            <Navbar />
            {cards}
        </div>
    )
}

```
### Vid 24
- Challenge:
    1. Display the correct text in the badge based on the logic above
    2. Only display the badge if badgeText has a value
```jsx
// Card.js
// 'logic above'
import React from "react"

export default function Card(props) {
    let badgeText
    if (props.openSpots === 0) {
        badgeText = "SOLD OUT"
    } else if (props.location === "Online") {
        badgeText = "ONLINE"
    }
    
// Wrong
    return (
        <div className="card">
            {props.openSpots === 0 && <div className="card--badge">SOLD OUT</div>}
            <img src={`../images/${props.img}`} className="card--image" />
            <div className="card--stats">
                <img src="../images/star.png" className="card--star" />
                <span>{props.rating}</span>
                <span className="gray">({props.reviewCount}) • </span>
                <span className="gray">{props.location}</span>
            </div>
            <p className="card--title">{props.title}</p>
            <p className="card--price"><span className="bold">From ${props.price}</span> / person</p>
        </div>
    )
}    

// Right
    return (
        <div className="card">
            {badgeText && <div className="card--badge">{badgeText}</div>}
            <img src={`../images/${props.img}`} className="card--image" />
            <div className="card--stats">
                <img src="../images/star.png" className="card--star" />
                <span>{props.rating}</span>
                <span className="gray">({props.reviewCount}) • </span>
                <span className="gray">{props.location}</span>
            </div>
            <p className="card--title">{props.title}</p>
            <p className="card--price"><span className="bold">From ${props.price}</span> / person</p>
        </div>
    )
}
```
### Vid 25
- I wasn't able to figure this one out. So I just watched the video and learned from trial and error. 
### Vid 26
- ES6 syntax explanation of how to use the spread operator that I'd already covered in Mod 2.
