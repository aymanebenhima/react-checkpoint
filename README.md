# React Checkpoint

<details open>
  <summary>Table of Contents</summary>

- [React JS Fundamentals](#react-js-fundamentals)
  - [Objective 1: Product Card Display](#objective-1-product-card-display)
- [React State](#react-state)
  - [Objective: Class-Based Component with State](#objective-class-based-component-with-state)
- [React Hooks](#react-hooks)
  - [Objective: Movie App with React Hooks](#objective-movie-app-with-react-hooks)
  
</details>

---

## React JS Fundamentals

<details>
  <summary>Objective 1: Product Card Display</summary>

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
   - Define a JSON object with keys: `name`, `price`, `description`, and `image`.
     ```javascript
     // src/product.js
     const product = {
       name: "Wireless Headphones",
       price: "$99.99",
       description: "High-quality wireless headphones with noise-cancellation.",
       image: "https://via.placeholder.com/150"
     };

     export default product;
     ```

4. **Create Individual Components**
   - Create four files in the `src` folder:
     - `Name.js`
     - `Price.js`
     - `Description.js`
     - `Image.js`

   - Each file should contain a React component displaying the respective property from the product object.
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
       const firstName = "John";

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

---

## React State

<details>
  <summary>Objective: Class-Based Component with State</summary>

### Overview
In this checkpoint, you will create your first class-based React component and implement state management within this component. Your goal is to build an application that displays a person's profile with details like `fullName`, `bio`, `imgSrc`, and `profession`. Additionally, you'll implement a button to toggle the visibility of this profile and show a field displaying the time elapsed since the component was mounted using React lifecycle methods.

### Prerequisites

Before you begin, ensure that you have:
- Node.js and npm installed.
- Basic knowledge of React and JavaScript.

### Project Setup Instructions

1. **Create a New React App**
   - Use the `create-react-app` command to set up a new project.
     ```bash
     npx create-react-app my-class-based-component
     cd my-class-based-component
     ```

2. **Transform `App.js` into a Class-Based Component**
   - Change the default `App` function component in `App.js` to a class-based component by extending `React.Component`.

3. **Implement State in the Class Component**
   - Create a state object within your class component:
     ```jsx
     state = {
       person: {
         fullName: 'Your Full Name',
         bio: 'Short bio about the person',
         imgSrc: 'path/to/your/image.jpg',
         profession: 'Your Profession'
       },
       shows: false,
       mountedTime: 0
     };
     ```

4. **Add a Button to Toggle Visibility**
   - Add a button to toggle the `shows` state when clicked.
   - Display the profile only if `shows` is `true`.

5. **Show the Time Interval Since the Component Was Mounted**
   - Use React lifecycle methods like `componentDidMount` and `componentWillUnmount` to manage a timer.

## Hints

- Use `setState` to update the `shows` state.
- Use `componentDidMount` to start a timer using `setInterval` and `componentWillUnmount` to clear the timer.

</details>

---

## React Hooks

<details>
  <summary>Objective: Movie App with React Hooks</summary>

### Overview
Create a simple movie app that allows users to showcase their favorite movies or TV shows. The app will utilize React hooks for state management and functional components. You will also implement features to add new movies and filter movies based on their title and rating.

### Components to Create

1. **MovieCard**  
   Display details of a single movie including Title, Description, Poster, and Rating.

2. **MovieList**  
   Render a list of movies using the `MovieCard` component.

3. **Filter**  
   Provide inputs for filtering movies by title and rating.

### Features to Implement

- **Add a New Movie**  
  Create a form to allow users to add a new movie...

</details>
