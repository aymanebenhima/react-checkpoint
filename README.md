# React Checkpoint

<details open>
  <summary>Table of Contents</summary>

- [React JS Fundamentals](#react-js-fundamentals)
  - [Objective 1: Product Card Display](#objective-1-product-card-display)
  - [Objective 2: FIFA Player Cards](#objective-2-fifa-player-cards)
- [React State](#react-state)
  - [Objective: Class-Based Component with State](#objective-class-based-component-with-state)
- [React Hooks](#react-hooks)
  - [Objective: Movie App with React Hooks](#objective-movie-app-with-react-hooks)
- [React Debugging](#react-debugging)
  - [Objective: Debug a sample React application](#objective-debug-a-sample-react-application)
- [React API](#react-api)
  - [Objective: Consuming an API and Displaying a List of Users](#objective-consuming-an-api-and-displaying-a-list-of-users)
- [React Router](#react-router)
  - [Objective: Adding Routing to Your Movie App](#objective-adding-routing-to-your-movie-app)
- [Managing State in React](#managing-state-in-react)
  - [Objective: Managing State To-Do List Application](#objective-managing-state-to-do-list-application)
- [Redux](#redux)
  - [Objective: Redux To-Do Application](#objective-redux-to-do-application)
  
</details>

---
<details>
<summary>React JS Fundamentals</summary>

## Objective 1: Product Card Display

### Overview
In this checkpoint, we will use React components and JSX to create a product card application using structured data and components. This checkpoint will enhance your skills with React components, JSX, data props, and React Bootstrap for styling.

### Instructions

1. **Create a React Project**
   - Use `create-react-app` to create a new React project:
     ```bash
     npx create-react-app product-card
     ```
   - Navigate to your project directory:
     ```bash
     cd product-card
     ```

2. **Create the App Component**
   - Inside the `src` folder, create a file `App.js` if it doesn't already exist.
   - This will be your root component.

3. **Create a Product Data File**
   - Create a file named `product.js` in the `src` folder.
   - Define a JSON object with the following keys: `name`, `price`, `description`, and `image`.
     ```javascript
     // src/product.js
     const product = {
       name: "Wireless Headphones",
       price: "$99.99",
       description: "High-quality wireless headphones with noise-cancellation.",
       image: "https://via.placeholder.com/150" // Replace with any valid URL
     };

     export default product;
     ```

4. **Create Individual Components**
   - Create four files in the `src` folder:
     - `Name.js`
     - `Price.js`
     - `Description.js`
     - `Image.js`

   - Each file should contain a React component that displays the respective property from the product object.
     Example for `Name.js`:
     ```javascript
     // src/Name.js
     import React from 'react';
     import product from './product';

     const Name = () => {
       return <h2>{product.name}</h2>;
     };

     export default Name;
     ```
   - Follow a similar structure for `Price.js`, `Description.js`, and `Image.js`.

5. **Import and Use Components in App.js**
   - In `App.js`, import the components and create a product card using React Bootstrap:
     ```javascript
     // src/App.js
     import React from 'react';
     import Name from './Name';
     import Price from './Price';
     import Description from './Description';
     import Image from './Image';
     import 'bootstrap/dist/css/bootstrap.min.css';

     function App() {
       const firstName = "John"; // Replace with your name or keep it blank

       return (
         <div className="container mt-5">
           <div className="card" style={{ width: '18rem' }}>
             <Image />
             <div className="card-body">
               <Name />
               <Price />
               <Description />
             </div>
           </div>
           <p className="mt-3">
             {firstName ? `Hello, ${firstName}!` : 'Hello, there!'}
           </p>
           {firstName && <img src="https://via.placeholder.com/100" alt="Optional Image" />}
         </div>
       );
     }

     export default App;
     ```

### Hints
- Use `import` statements to bring your components into `App.js`.
- Use React Bootstrap classes like `card`, `card-body`, etc., for styling.
- Feel free to add more styling using inline styles or CSS classes.

## Objective 2: FIFA Player Cards

### Overview
In this checkpoint, you will create a React app to display a list of FIFA player cards. This exercise will enhance your ability to work with arrays, components, props, and styling in React.

### Instructions

1. **Create a React Project**
   - Use `create-react-app` to create a new project:
     ```bash
     npx create-react-app fifa-players
     ```
   - Navigate to your project directory:
     ```bash
     cd fifa-players
     ```

2. **Create Player Data File**
   - Create a file named `players.js` in the `src` folder.
   - Define an array of objects, each representing a player with attributes: `name`, `team`, `nationality`, `jerseyNumber`, `age`, and `image`.
     ```javascript
     // src/players.js
     const players = [
       {
         name: "Player 1",
         team: "Team A",
         nationality: "Country A",
         jerseyNumber: 7,
         age: 27,
         image: "https://via.placeholder.com/150"
       },
       {
         name: "Player 2",
         team: "Team B",
         nationality: "Country B",
         jerseyNumber: 10,
         age: 30,
         image: "https://via.placeholder.com/150"
       },
       // Add more players as desired
     ];

     export default players;
     ```

3. **Create Player Component**
   - Create a file named `Player.js`:
     ```javascript
     // src/Player.js
     import React from 'react';
     import PropTypes from 'prop-types';
     import 'bootstrap/dist/css/bootstrap.min.css';

     const Player = ({ name, team, nationality, jerseyNumber, age, image }) => {
       const cardStyle = {
         margin: '10px',
         padding: '15px',
         textAlign: 'center',
       };

       return (
         <div className="card" style={{ width: '18rem', ...cardStyle }}>
           <img src={image} className="card-img-top" alt={name} />
           <div className="card-body">
             <h5 className="card-title">{name}</h5>
             <p className="card-text">
               Team: {team} <br />
               Nationality: {nationality} <br />
               Jersey Number: {jerseyNumber} <br />
               Age: {age}
             </p>
           </div>
         </div>
       );
     };

     Player.propTypes = {
       name: PropTypes.string.isRequired,
       team: PropTypes.string.isRequired,
       nationality: PropTypes.string.isRequired,
       jerseyNumber: PropTypes.number.isRequired,
       age: PropTypes.number.isRequired,
       image: PropTypes.string.isRequired,
     };

     Player.defaultProps = {
       name: 'Unknown Player',
       team: 'Unknown Team',
       nationality: 'Unknown',
       jerseyNumber: 0,
       age: 0,
       image: 'https://via.placeholder.com/150',
     };

     export default Player;
     ```

4. **Create PlayersList Component**
   - Create a file named `PlayersList.js`:
     ```javascript
     // src/PlayersList.js
     import React from 'react';
     import Player from './Player';
     import players from './players';

     const PlayersList = () => {
       return (
         <div className="d-flex flex-wrap justify-content-center">
           {players.map((player) => (
             <Player key={player.name} {...player} />
           ))}
         </div>
       );
     };

     export default PlayersList;
     ```

5. **Use PlayersList Component in App.js**
   - Import and render the `PlayersList` component in `App.js`:
     ```javascript
     // src/App.js
     import React from 'react';
     import PlayersList from './PlayersList';

     function App() {
       return (
         <div className="App">
           <h1 className="text-center">FIFA Players</h1>
           <PlayersList />
         </div>
       );
     }

     export default App;
     ```

### Hints
- Use `map` to iterate through the array of players and render a `Player` component for each player.
- Use the spread operator to pass props to the `Player` component.
- Add custom styling using inline styles for the `Player` component.
</details>

<details>
<summary>React State</summary>

## Objective: Class-Based Component with State

In this checkpoint, you will create your first class-based React component and implement state management within this component. Your goal is to build an application that displays a person's profile with details like `fullName`, `bio`, `imgSrc`, and `profession`. Additionally, you'll implement a button to toggle the visibility of this profile and show a field displaying the time elapsed since the component was mounted using React lifecycle methods.

## Prerequisites

Before you begin, ensure that you have:
- Node.js and npm installed.
- Basic knowledge of React and JavaScript.

## Project Setup Instructions

1. **Create a New React App**
   - Use the `create-react-app` command to set up a new project.
     ```bash
     npx create-react-app my-class-based-component
     cd my-class-based-component
     ```

2. **Transform `App.js` into a Class-Based Component**
   - Change the default `App` function component in `App.js` to a class-based component by extending `React.Component`.

3. **Implement State in the Class Component**
   - Create a state object within your class component with the following properties:
     ```jsx
     state = {
       person: {
         fullName: 'Your Full Name',
         bio: 'Short bio about the person',
         imgSrc: 'path/to/your/image.jpg',
         profession: 'Your Profession'
       },
       shows: false,
       mountedTime: 0 // To track elapsed time since component mount
     };
     ```

4. **Add a Button to Toggle Visibility**
   - Add a button in the render method to toggle the `shows` state when clicked.
   - When `shows` is `true`, display the person's profile. Otherwise, hide it.

5. **Display the Person's Profile Conditionally**
   - Use conditional rendering to display the person's information based on the value of `shows`.
   - Display the following fields:
     - Full Name
     - Bio
     - Image (use an `img` element)
     - Profession

6. **Show the Time Interval Since the Component Was Mounted**
   - Implement React lifecycle methods such as `componentDidMount` and `componentWillUnmount` to start and clear a timer using `setInterval`.
   - Display the elapsed time in seconds since the component was mounted.

## Hints

- **Class-Based Components**: Remember that class components extend `React.Component` and have access to lifecycle methods and `state`.
- **State Initialization**: You can initialize the state object in the constructor or directly within the class body.
- **Toggling Visibility**: Use the `setState` method to update the `shows` state when the button is clicked.
  ```jsx
  this.setState({ shows: !this.state.shows });
  ```
- **Lifecycle Methods**:
  - `componentDidMount` is a good place to start the timer using `setInterval`.
  - `componentWillUnmount` can be used to clear the timer when the component is unmounted.
- **Conditional Rendering**: Use a ternary operator or `&&` logical operator to conditionally render JSX elements based on the `shows` state.

## Example Project Structure

```bash
my-class-based-component/
├── README.md
├── node_modules
├── package.json
├── public
└── src
    ├── App.js
    ├── index.js
    └── index.css
```

---

## Additional Tips

- Use appropriate CSS classes to style your component for a better UI/UX.
- Ensure that you handle state updates correctly without directly mutating the state.
- For better accessibility, make sure the toggle button has a descriptive label.
</details>

<details>
<summary>React Hooks</summary>

## Objective: Movie App with React Hooks

In this checkpoint, your task is to create a simple movie app that allows users to showcase their favorite movies or TV shows. The app will utilize React hooks for state management and functional components. You'll also implement features to add new movies and filter movies based on their title and rating.

## Instructions

### Components to Create

1. **MovieCard**  
   This component will display the details of a single movie. Each movie card should show:
   - Title
   - Description
   - Poster (using `posterURL`)
   - Rating

2. **MovieList**  
   This component will:
   - Render a list of movies.
   - Take the list of movies as a prop and map through it to display each movie using the `MovieCard` component.

3. **Filter**  
   This component will allow the user to:
   - Filter movies by their title.
   - Filter movies by their rating.
   - It will take input values (title and rating) and pass them to a function that filters the movie list in the `MovieList` component.

### Features to Implement

- **Add a New Movie**  
  Create a form or input fields that allow users to add a new movie with the following attributes:
  - Title
  - Description
  - Poster URL
  - Rating

- **Filtering Movies**  
  Allow the user to filter movies based on:
  - **Title:** Filter should be case-insensitive and partial matches should be considered.
  - **Rating:** Filter should show movies with ratings greater than or equal to the selected rating.

## Project Setup Instructions

### 1. Create a New React App

- If you haven't already, set up a new React project:
  ```bash
  npx create-react-app movie-app
  cd movie-app
  ```
  
### 2. Create Components

- Create the necessary components (`MovieCard`, `MovieList`, `Filter`) inside the `src` folder.

### 3. Use React Hooks

- Use **React hooks** (`useState`, `useEffect`, etc.) to manage component state and handle user interactions.

## Hints

### State Management

- **State for Movies:** Use `useState` to create a state variable that holds an array of movie objects.
  ```jsx
  const [movies, setMovies] = useState([
    // Example movie object
    {
      title: "Example Movie",
      description: "An example movie description.",
      posterURL: "https://example.com/poster.jpg",
      rating: 5
    }
  ]);
  ```
  
- **Adding a New Movie:** You can create a function that updates the `movies` state with a new movie object. Consider using an input form and `onChange`/`onSubmit` handlers.

### Filtering Movies

- **Filter by Title:** Create a state variable for the filter input and use it to conditionally render the movie list based on the input value.
- **Filter by Rating:** Similarly, use a state variable for rating input and display movies that match the criteria.

### Conditional Rendering

- Make sure to use conditional rendering to display messages like "No movies found" when the filtered list is empty.

### CSS Styling

- Add styles to make your app visually appealing using CSS or any library of your choice (e.g., Tailwind CSS, Bootstrap).

### Example Project Structure

```bash
movie-app/
├── README.md
├── node_modules
├── package.json
├── public
└── src
    ├── App.js
    ├── components
    │   ├── MovieCard.js
    │   ├── MovieList.js
    │   └── Filter.js
    ├── index.js
    └── App.css
```

## Criteria for Evaluation

- **Respect of the Guidelines:** Ensure that you follow the project instructions.
- **Use of Hooks:** Proper usage of React hooks like `useState` and `useEffect`.
- **Filtering Functionality:** The filtering by title and rating should work as expected.
- **Adding Movies:** Users should be able to add new movies using a form or input fields.

## Additional Tips

- **Reusable Components:** Consider making `MovieCard` a reusable component that can be used in different contexts if needed.
- **Performance Optimization:** Avoid unnecessary re-renders by using memoization techniques if applicable.
- **Accessibility:** Make sure to add appropriate `aria` labels and handle keyboard interactions for better accessibility.
</details>

<details>
<summary>React Debugging</summary>

## Objective: Debug a sample React application
Debug a sample React application using the React Developer Tools to identify and resolve issues such as incorrect state values, missing props, or unexpected component behavior.

### Checkpoint Description
In this checkpoint, you will focus on enhancing your debugging skills with React by leveraging the React Developer Tools. This challenge will provide you with valuable experience in diagnosing and fixing common React issues related to state, props, and component behavior.

### Instructions

1. **Set Up the Sample Application**
   - Use the provided sample React application or create a simple one with multiple components.
   - Ensure it contains examples of state management (using `useState` or `useReducer`) and prop passing between components.

2. **Install React Developer Tools**
   - If you have not already done so, install the [React Developer Tools browser extension](https://react.devtools) for Chrome, Firefox, or Edge. Alternatively, you can use the standalone version.
   - Here's the buggy code:
  ```jsx
import React, { useState } from "react";
import CounterDisplay from "./CounterDisplay";
import CounterControls from "./CounterControls";

function App() {
  const [counter, setCounter] = useState(0);

  // Function to increment counter
  const increment = () => setCounter(counter + 1);

  // Function to decrement counter
  const decrement = () => setCounter(counter - 1);

  // Function to reset counter
  const reset = () => setCounter(0);

  return (
    <div>
      <h1>Debug the Counter App</h1>
      {/* Passing props to child components */}
      <CounterDisplay counter={counter} />
      <CounterControls
        onIncrement={increment}
        onDecrement={decrement}
        onReset={reset}
      />
    </div>
  );
}

export default App;

// CounterDisplay.jsx
import React from "react";

function CounterDisplay({ value }) {
  return (
    <div>
      <h2>Current Counter: {value}</h2>
    </div>
  );
}

export default CounterDisplay;

// CounterControls.jsx
import React from "react";

function CounterControls({ onIncrement, onDecrement }) {
  return (
    <div>
      <button onClick={onIncrement}>Increment</button>
      <button onClick={onDecrement}>Decrement</button>
      <button onClick={onReset}>Reset</button>
    </div>
  );
}

export default CounterControls;
```
- *Objective:*
  - Identify the bugs in the app and fix them.
  - Debug the following:
  - Why the counter value doesn’t display correctly.
  - Why the "Reset" button causes an error.
  - Explain how React Developer Tools can be used to debug this app.
 
- *Instructions:*
  - Inspect the App Component:
    - Use React DevTools to check the counter state in the App component.
    - Confirm that the counter state updates correctly when the buttons are clicked.
  - Inspect the CounterDisplay Component:
    - Check the props passed to the CounterDisplay component.
    - Identify why the counter value is not displayed.
  - Inspect the CounterControls Component:
    - Verify the props (onIncrement, onDecrement, onReset) passed to CounterControls.
    - Find the source of the error when the "Reset" button is clicked.
  - Fix the Bugs:
    - Update the code to fix the issues.


3. **Inspect the Components Tree**
   - Open your application in the browser.
   - Access the React Developer Tools by navigating to the Developer Tools panel (often available under "Components" in the DevTools tab).

4. **Identify Issues**
   - Look for components displaying unexpected behavior (e.g., rendering errors, incorrect state values, missing props, or warnings in the console).
   - Expand the component tree and inspect the state and props of individual components.
   - Note down any discrepancies, such as:
     - **Incorrect state values**: Is the state different from what you expect?
     - **Missing or incorrect props**: Are required props missing or being passed incorrectly?
     - **Unexpected rendering behavior**: Are components re-rendering too often or not rendering at all?

5. **Diagnose the Problems**
   - Use the features in React Developer Tools:
     - **State and Props Inspection**: Hover over or click on components to view their props and state values.
     - **Hooks Inspector**: If your component uses hooks, view their current state.
     - **Profiler**: Analyze component render times and detect performance bottlenecks.
     - **Highlight Updates**: Enable highlighting to see which components are re-rendering.

6. **Fix the Issues**
   - Apply fixes in the codebase based on your diagnosis:
     - **State Issues**: Ensure state changes are being handled correctly (e.g., avoid mutating state directly).
     - **Props Issues**: Double-check parent-to-child prop passing.
     - **Rendering Behavior**: Address any unnecessary renders by using memoization, React.memo, or fine-tuning dependencies in `useEffect`.

7. **Document the Debugging Process**
   - Keep a log of the steps you followed, issues identified, and the solutions implemented.
   - Summarize any useful insights gained from using the React Developer Tools.

8. **Verify Functionality**
   - Test the application thoroughly to ensure the issues have been resolved and no new issues were introduced.
   - Use the browser console to double-check for any lingering warnings or errors.

---

### Hints

- **State Inspection**: When inspecting state, watch for direct state mutations (e.g., modifying arrays or objects without creating a new copy).
- **Component Re-renders**: If a component re-renders unexpectedly, check if it receives new props or if its state changes due to a parent component's update.
- **Props Validation**: Use `PropTypes` or TypeScript to validate prop types in components, which can help identify missing or incorrect props.
- **Hooks Dependencies**: Ensure that `useEffect` dependencies are correctly specified to prevent infinite loops or missed updates.
- **Avoid "Magic" Fixes**: If you "fix" a problem without fully understanding it, take the time to investigate. Issues may reappear or lead to other unexpected behavior later.
- **Profile for Performance**: Use the React Profiler to identify slow components, which may be caused by frequent or unnecessary renders.
</details>

<details>
<summary>React API Checkpoint</summary>

## Objective: Consuming an API and Displaying a List of Users

In this checkpoint, the goal is to build a React application that consumes an API to retrieve and display a list of users. By completing this task, you will strengthen your skills in API consumption, React state management, and component lifecycle handling using hooks.

## Instructions

### Step-by-Step Guide

1. **Project Setup**:
   - Create a new React project using `create-react-app` by running the following command in your terminal:
     ```bash
     npx create-react-app react-api-checkpoint
     ```
   - Navigate to your project directory:
     ```bash
     cd react-api-checkpoint
     ```

2. **File Creation**:
   - In the `src` folder of your project, create a new file named `UserList.js`. This file will contain the logic to fetch and display the list of users.

3. **Install Axios**:
   - Install Axios for making HTTP requests. Run the following command:
     ```bash
     npm install axios
     ```

4. **Fetch Data from API**:
   - You will use the [JSONPlaceholder](https://jsonplaceholder.typicode.com/users) API to get a list of users.
   - Inside the `UserList.js` file, use the `axios` library to fetch the data within a `useEffect` hook.

5. **State Management**:
   - Use the `useState` hook to store the fetched list of users in a state variable named `listOfUser`.

6. **Display Data**:
   - Map over `listOfUser` to display the list of users on the screen. Ensure to create user-friendly output.

7. **Style the Application**:
   - Add custom styles to enhance the appearance of the application as per your preference.

## Example Structure for `UserList.js`

```javascript
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserList() {
  // Step 5: State for storing users
  const [listOfUser, setListOfUser] = useState([]);

  // Step 4: Fetching data using useEffect
  useEffect(() => {
    axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        // Save data to state
        setListOfUser(response.data);
      })
      .catch(error => {
        console.error('There was an error fetching the data!', error);
      });
  }, []);

  // Step 6: Render the list of users
  return (
    <div>
      <h1>List of Users</h1>
      <ul>
        {listOfUser.map(user => (
          <li key={user.id}>
            <strong>{user.name}</strong> - {user.email}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```

### Hints

1. **Project Creation**: If you're unfamiliar with `create-react-app`, it is a handy tool to quickly bootstrap a React application with all necessary configurations.

2. **Component Lifecycle**: Remember that the `useEffect` hook runs after the component mounts. If you need to fetch data when the component loads, you should place your API call within this hook.

3. **State Management**: Ensure you are familiar with the `useState` hook for managing state. In this example, `listOfUser` holds the fetched user data.

4. **Handling Promises**: Remember that `axios.get()` returns a promise. Use `.then()` and `.catch()` to handle the promise and any potential errors.

5. **Mapping Data**: When mapping through `listOfUser` to display the user data, ensure each child element has a unique `key` prop (usually `user.id` is a good candidate).

6. **Styling**: You can use plain CSS, CSS modules, or even styled-components to style your application. Take advantage of modern styling techniques to create a user-friendly interface.

---

## Checkpoint Criteria

### Evaluation Metrics (Rated 1-5)
- **Respect of the Guidelines**: Have you followed all specified steps in the instructions?
- **Use of Hooks**: Have you correctly used the `useEffect` and `useState` hooks for fetching and managing state?
- **Application Styling**: Does the application have a visually appealing style? Have you applied custom styling as suggested? 
</details>

<details>
<summary>React Router</summary>

## Objective: Adding Routing to Your Movie App

In this checkpoint, we will enhance the movie app created in the previous checkpoint by integrating React Router. Our goal is to enable routing for navigating between a home page that displays movie cards and a description page for each movie, complete with a trailer video. The description page should also provide a way to navigate back to the home page.

## Instructions

### Step-by-Step Guide

1. **Enhance the Movie Object**:
   - Add two new properties to your movie object: `description` (text) and `trailerLink` (embedded video URL). You will display these on the movie description page.

2. **Install React Router**:
   - Install React Router to handle routing in your React application. Use the following command:
     ```bash
     npm install react-router-dom
     ```

3. **Set Up Routes**:
   - Import `BrowserRouter`, `Route`, and `Link` from `react-router-dom`.
   - Set up a route for the home page that displays the movie cards, and another route for the movie description page that displays the details and trailer of a selected movie.

4. **Movie Card Navigation**:
   - Make each movie card clickable. When clicked, the user should be navigated to a separate page that displays the movie's description and trailer.
   - Use the `Link` component from `react-router-dom` to enable navigation from the movie card to the movie description page.

5. **Description Page**:
   - On the movie description page, display the movie's description and embed the trailer video from the `trailerLink` property.
   - Implement a "Back" button on the description page that allows the user to return to the home page.

6. **Home Page Navigation**:
   - Implement a "Back" button on the description page that navigates back to the home page. Use `useNavigate` from React Router to implement this functionality.

### Example Structure for `App.js`

```javascript
import React, { useState } from 'react';
import { BrowserRouter as Router, Route, Routes, Link, useNavigate } from 'react-router-dom';

// Sample movie data
const movies = [
  { id: 1, name: 'Movie 1', description: 'This is movie 1.', trailerLink: 'https://www.youtube.com/embed/video1' },
  { id: 2, name: 'Movie 2', description: 'This is movie 2.', trailerLink: 'https://www.youtube.com/embed/video2' },
  // Add more movies as needed
];

function Home() {
  return (
    <div>
      <h1>Movie List</h1>
      <div>
        {movies.map(movie => (
          <div key={movie.id}>
            <h2>{movie.name}</h2>
            <Link to={`/movie/${movie.id}`}>View Details</Link>
          </div>
        ))}
      </div>
    </div>
  );
}

function MovieDescription({ movieId }) {
  const movie = movies.find(m => m.id === parseInt(movieId));
  const navigate = useNavigate();

  return (
    <div>
      <h1>{movie.name}</h1>
      <p>{movie.description}</p>
      <iframe width="560" height="315" src={movie.trailerLink} title="Trailer" frameBorder="0" allowFullScreen></iframe>
      <br />
      <button onClick={() => navigate('/')}>Back to Home</button>
    </div>
  );
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="movie/:movieId" element={<MovieDescription />} />
      </Routes>
    </Router>
  );
}

export default App;
```

### Hints

1. **Movie Object Enhancement**:
   - Ensure your movie object contains the necessary fields (`description`, `trailerLink`) that you will use for the movie description page.
   
2. **React Router Setup**:
   - The `BrowserRouter` component wraps your entire app and handles URL history.
   - `Routes` is used to define all the routes in your app, and `Route` specifies the path and the component that should render for that path.

3. **Dynamic Routing**:
   - Use the `useParams` hook to access dynamic values in the URL, such as the movie ID. This is important for rendering the correct movie description page.

4. **Linking to the Description Page**:
   - The `Link` component is a wrapper for anchor tags that enables navigation without reloading the page. It should point to the dynamic URL for the movie's description page (`/movie/:movieId`).

5. **Navigate Back**:
   - Use the `useNavigate` hook to programmatically navigate between pages. This is useful for implementing the "Back" button functionality.

6. **Embedding YouTube Video**:
   - You can embed the trailer using an `<iframe>` tag. The `src` attribute of the iframe should point to the `trailerLink` from the movie object.

---

## Checkpoint Criteria

### Evaluation Metrics (Rated 1-5)
- **Trailer Link Added**: Did you add a valid trailer link (video URL) to each movie object?
- **Movie Description**: Is the movie description properly displayed on the description page?
- **"Back" Button**: Does the "Back" button work correctly and return the user to the home page?

</details>

<details>
<summary>Managing State in React</summary>

## Objective: Managing State To-Do List Application

In this checkpoint, you will build a **To-Do List** application using React. The application will demonstrate how to manage state and handle various actions such as adding, editing, deleting, and marking tasks as completed. Additionally, you'll implement form validation and persist the tasks using browser storage to maintain the state across sessions.

## Features

1. **Form Validation**: Ensure that the task name and description fields are filled before adding or editing a task.
2. **State Management**: Use React's state management to keep track of the list of tasks and their completion status.
3. **Task Actions**: Implement functionality to add, edit, delete, and mark tasks as completed.
4. **Persistence**: Use browser storage (`localStorage` or `sessionStorage`) to persist tasks across sessions.
5. **Styling**: Make the application visually appealing and user-friendly with appropriate CSS styling.
6. **Optional Features**: Implement additional features such as filtering tasks or adding due dates.

## Instructions

### 1. **Create the Task List**

Create a task list where each task has:
- **Name**
- **Description**
- **Completion status** (active or completed)

### 2. **Implement a Task Form**
- The form should allow users to add new tasks. It should contain:
  - Input fields for **task name** and **task description**.
  - Validation to ensure both fields are filled out before submitting.
  - If validation fails, display an error message.
  
- The form should also allow editing an existing task. When editing, pre-fill the form with the task's current details (name and description).

### 3. **Display Task List**
- Display all tasks in a list.
- Each task should have:
  - A button to mark it as **completed** (which toggles its status).
  - An **Edit** button that allows the user to modify the task's details.
  - A **Delete** button that prompts the user for confirmation before deleting the task.

### 4. **Manage State**
- Use React state hooks to:
  - Store the list of tasks.
  - Track which task is currently being edited.
  - Track whether a task is completed or not.

### 5. **Use Browser Storage for Persistence**
- Use either `localStorage` or `sessionStorage` to persist the list of tasks.
- On page load, check if tasks are stored in browser storage. If so, load them into the state.
- When tasks are added, edited, or deleted, save the updated task list to browser storage.

### 6. **Style the Application**
- Use CSS to create a simple and visually appealing layout.
- Active tasks should look different from completed tasks (e.g., strike-through for completed tasks).

### 7. **Optional Features**
- **Filtering**: Implement filtering to display either active tasks, completed tasks, or all tasks.
- **Sorting**: Allow sorting tasks based on priority or due date (if applicable).
- **Due Dates**: Add an optional field for due dates on tasks and allow sorting by the due date.

---

## Hints

1. **React State Management**:
   - Use `useState` to manage tasks.
   - Use `useEffect` to load tasks from browser storage when the app initializes.
   - Use `useState` to track the current task being edited.

2. **Form Validation**:
   - Implement a simple check before adding a new task or editing an existing one. For example, you could check that both the task name and description are non-empty before allowing the form to submit.
   - You could conditionally render an error message if the validation fails.

3. **Handling Completion Status**:
   - Use a `completed` flag for each task. When a user clicks the "Mark as Completed" button, toggle the `completed` flag.
   - Apply different CSS styles to completed tasks (e.g., strike-through or change color).

4. **Task Actions**:
   - Use a button inside each task item to toggle its completion status (`onClick` event).
   - Use a button to allow the user to edit or delete tasks. For editing, pre-fill the form with the task's current details.

5. **Persistence**:
   - Use `localStorage` to store tasks. For example:
     ```javascript
     localStorage.setItem('tasks', JSON.stringify(tasks));
     ```
   - On app load, check if there are tasks saved in `localStorage`:
     ```javascript
     const savedTasks = JSON.parse(localStorage.getItem('tasks'));
     if (savedTasks) {
       setTasks(savedTasks);
     }
     ```

6. **Confirmation for Deletion**:
   - Use the `window.confirm()` method to ask the user for confirmation before deleting a task.

---

## Example Folder Structure

```
src/
  components/
    TaskList.js        // Displays the list of tasks
    TaskForm.js        // Form for adding and editing tasks
    TaskItem.js        // Represents each task (with options to edit, delete, and toggle completion)
  App.js               // Main App component that ties everything together
  index.js             // Entry point
  styles.css           // Styling for the application
```

## Checkpoint Criteria

- **Form Validation**: Ensure that both task name and description fields are validated.
- **State Management**: The list of tasks should be correctly managed using React state and updated when tasks are added, edited, or deleted.
- **Task Actions**: Implement proper functionality for marking tasks as completed, editing, and deleting tasks.
- **Persistence**: Ensure that the task list is saved to browser storage and is persistent across sessions.
- **Styling**: The application should have a simple but appealing UI, with active and completed tasks visually distinguished.

---

## How to Run Locally

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <project-folder>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

4. Open the application in your browser at `http://localhost:3000`.

</details>

<details>
<summary>Redux</summary>

## Objective: Redux To-Do Application

In this checkpoint, you will create a **To-Do Application** using **Redux** to manage the global state of your application. You will implement key features such as adding new tasks, editing tasks, and filtering tasks based on their status (done or not). This will help you learn how to integrate Redux for managing state across components in a React app.

## Features

1. **Add Task**: Ability to add new tasks with a description and status.
2. **Edit Task**: Allow users to edit an existing task's description.
3. **Filter Tasks**: Filter tasks by their status (completed or not).
4. **State Management with Redux**: Use Redux to manage global state for tasks.
5. **Task Status**: Track the status of each task (done or not).

## Instructions

### 1. **Set up Redux Store**

You will need to set up Redux to manage the state of your tasks globally. Here's a quick overview of the steps:

- **Install Redux and React-Redux**:
  ```bash
  npm install redux react-redux
  ```

- **Create Redux Actions**: You'll need actions to add a task, edit a task, and filter tasks.

- **Create Redux Reducers**: The reducer will handle the logic for updating the state based on dispatched actions.

- **Create Redux Store**: The store will hold the application state, and you'll need to use `Provider` from `react-redux` to make the store available to the app.

### 2. **Components to Implement**

- **AddTask**: 
  - This component will allow the user to input a new task description and add it to the global state.
  - It should dispatch an action to add the task to the Redux store.
  
- **ListTask**: 
  - This component will display the list of tasks. It will map through the state (tasks) and display each task using the `Task` component.
  
- **Task**:
  - This component will display each individual task, including the task description and its completion status.
  - It will have an "Edit" button to modify the task description and a "Complete" button to toggle the completion status.

### 3. **Task Attributes**

Each task will have the following attributes:
- `id`: A unique identifier for each task.
- `description`: A text field describing the task.
- `isDone`: A boolean indicating whether the task is completed or not.

### 4. **User Actions**

The user should be able to:
1. **Add a new task**: Input a task description and click "Add".
2. **Filter tasks**: Filter the tasks based on their status (completed or not).
3. **Edit a task**: Modify the task's description.

### 5. **Task State Management with Redux**

1. **Create Actions**:
   - **ADD_TASK**: Adds a new task to the state.
   - **EDIT_TASK**: Edits an existing task.
   - **TOGGLE_TASK**: Toggles the task's completion status.
   - **FILTER_TASKS**: Filters tasks based on their completion status (done or not).

2. **Create Reducers**:
   - Handle the logic for updating the task list based on the dispatched actions.

3. **Create Store**:
   - Combine reducers (if necessary) and configure the Redux store.

4. **Connect React Components**:
   - Use `connect()` or `useSelector` and `useDispatch` hooks from `react-redux` to connect the components to the Redux store.

### 6. **Filter Tasks by Status**

- **Filter by Task Status**: Provide buttons or checkboxes for the user to filter tasks based on their completion status.
  - Show "All", "Completed", and "Incomplete" filters.
  - When a filter is applied, only the tasks matching the filter should be displayed.

### 7. **Task Editing**

- Allow users to click an "Edit" button for a task.
- When the user clicks "Edit", the task's description should become editable.
- After editing, dispatch an action to update the task in the Redux store.

---

## Hints

1. **Redux State Setup**:
   - Your Redux state should look something like this:
     ```javascript
     const initialState = {
       tasks: [],
       filter: 'all', // can be 'all', 'completed', or 'incomplete'
     };
     ```

2. **Actions and Reducers**:
   - Define actions like `ADD_TASK`, `EDIT_TASK`, `TOGGLE_TASK`, and `FILTER_TASKS`.
   - In your reducer, ensure that you handle updating the tasks when these actions are dispatched:
     ```javascript
     case 'ADD_TASK':
       return { ...state, tasks: [...state.tasks, action.payload] };
     case 'EDIT_TASK':
       return { 
         ...state,
         tasks: state.tasks.map(task => 
           task.id === action.payload.id ? { ...task, description: action.payload.description } : task
         )
       };
     case 'TOGGLE_TASK':
       return {
         ...state,
         tasks: state.tasks.map(task => 
           task.id === action.payload ? { ...task, isDone: !task.isDone } : task
         )
       };
     case 'FILTER_TASKS':
       return { ...state, filter: action.payload };
     ```

3. **Using `connect` or `useSelector` and `useDispatch`**:
   - Use `useSelector` to access the Redux state inside your components:
     ```javascript
     const tasks = useSelector(state => state.tasks);
     const filter = useSelector(state => state.filter);
     ```
   - Use `useDispatch` to dispatch actions:
     ```javascript
     const dispatch = useDispatch();
     dispatch({ type: 'ADD_TASK', payload: newTask });
     ```

4. **Filter Logic**:
   - In `ListTask`, based on the current `filter` value, you can conditionally render tasks:
     ```javascript
     const filteredTasks = tasks.filter(task => {
       if (filter === 'completed') return task.isDone;
       if (filter === 'incomplete') return !task.isDone;
       return true; // 'all'
     });
     ```

5. **CSS Styling**:
   - Style tasks to visually distinguish between completed and incomplete tasks (e.g., strike-through completed tasks).
   - Consider adding a simple form with an input field for adding new tasks and a dropdown or buttons for filtering.

---

## Example Folder Structure

```
src/
  actions/
    taskActions.js       // Redux action creators
  components/
    AddTask.js           // Component for adding tasks
    ListTask.js          // Component to list tasks
    Task.js              // Individual task component
  reducers/
    taskReducer.js       // Reducer for task-related actions
  store.js               // Redux store setup
  App.js                 // Main App component
  index.js               // Entry point
  styles.css             // Application styling
```

---

## Checkpoint Criteria

- **Number of Components**: Ensure that you have the required components (`AddTask`, `ListTask`, and `Task`).
- **Task Attributes**: Ensure that each task has an `id`, `description`, and `isDone` status.
- **Functionality**:
  - **Add Task**: New tasks can be added and appear in the task list.
  - **Edit Task**: Tasks can be edited by modifying their description.
  - **Task Filtering**: Users can filter tasks by their completion status (done or not).
  - **Toggle Task Completion**: Users can mark tasks as done or not done.
  
---

## How to Run Locally

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <project-folder>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

4. Open the application in your browser at `http://localhost:3000`.

</details>

Happy coding! 🚀
