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
