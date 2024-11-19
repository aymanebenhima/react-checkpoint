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
</details>
<details>
<summary>Objective 2: FIFA Player Cards</summary>

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

Happy coding! 🚀
