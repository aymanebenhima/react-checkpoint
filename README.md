# React Checkpoint

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

---

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

Happy coding! 🚀
