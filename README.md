# React-Interview-Topics
React Interview Prep: Comprehensive repository with React interview topics with explanations and examples. Ideal for web developers preparing for technical interviews.

### Theoretical Topics

1. **React Basics**
   - **What is React?**
     - React is a JavaScript library for building user interfaces. It allows developers to create large web applications that can update and render efficiently in response to data changes.
   - **JSX and its advantages**
     - JSX is a syntax extension that looks similar to HTML. It's used with React to describe what the UI should look like. JSX makes it easier to write and add HTML in React.
     ```jsx
     const element = <h1>Hello, world!</h1>;
     ```
   - **Virtual DOM vs Real DOM**
     - Virtual DOM is a lightweight copy of the real DOM. React uses the Virtual DOM to optimize updates and rendering, making apps faster.
   - **React Components (Functional vs Class)**
     - Components are the building blocks of a React application. Functional components are simpler and use hooks, while class components use lifecycle methods.
     ```jsx
     // Functional Component
     function Welcome(props) {
       return <h1>Hello, {props.name}</h1>;
     }
     
     // Class Component
     class Welcome extends React.Component {
       render() {
         return <h1>Hello, {this.props.name}</h1>;
       }
     }
     ```
   - **Props and State**
     - Props are inputs to a component, passed from parent to child. State is managed within the component and can change over time.
     ```jsx
     function Welcome(props) {
       return <h1>Hello, {props.name}</h1>;
     }

     class Clock extends React.Component {
       constructor(props) {
         super(props);
         this.state = { date: new Date() };
       }
     }
     ```
   - **Lifecycle Methods (Class components)**
     - Lifecycle methods allow you to run code at specific points in a component's lifecycle, like `componentDidMount` or `componentWillUnmount`.
     ```jsx
     componentDidMount() {
       // Runs after the component is rendered
     }
     ```
   - **Hooks (useState, useEffect, useContext, etc.)**
     - Hooks are functions that let you use state and other React features in functional components.
     ```jsx
     const [count, setCount] = useState(0);

     useEffect(() => {
       document.title = `You clicked ${count} times`;
     }, [count]);
     ```

2. **Component Communication**
   - **Passing data between components (Parent to Child, Child to Parent)**
     - Data can be passed from parent to child using props, and from child to parent using callback functions.
     ```jsx
     // Parent to Child
     <ChildComponent message="Hello" />
     
     // Child to Parent
     function ChildComponent(props) {
       props.onMessage("Hello from child");
     }
     ```
   - **Context API**
     - The Context API provides a way to share values between components without passing props through every level of the tree.
     ```jsx
     const MyContext = React.createContext();

     function MyProvider({ children }) {
       return (
         <MyContext.Provider value={/* some value */}>
           {children}
         </MyContext.Provider>
       );
     }
     ```
   - **Prop Drilling**
     - Prop drilling refers to passing props through multiple levels of components. It can be mitigated by using Context API or state management libraries.

3. **State Management**
   - **useState, useReducer**
     - `useState` is a hook for adding state to functional components. `useReducer` is used for complex state logic.
     ```jsx
     const [count, setCount] = useState(0);
     ```
   - **Context API**
     - Provides a way to manage global state that can be accessed by any component.
   - **Redux (Actions, Reducers, Store, Middleware)**
     - Redux is a state management library. It uses actions to describe changes, reducers to handle them, and a store to hold the state.
     ```jsx
     const store = createStore(reducer);
     ```

4. **React Router**
   - **Setting up routes**
     - React Router allows navigation between different components in a React application.
     ```jsx
     <Router>
       <Route path="/home" component={Home} />
       <Route path="/about" component={About} />
     </Router>
     ```
   - **Link vs NavLink**
     - `Link` is used for navigation, while `NavLink` provides additional styling options for active links.
     ```jsx
     <Link to="/home">Home</Link>
     <NavLink to="/about" activeClassName="active">About</NavLink>
     ```
   - **Route parameters**
     - Route parameters allow dynamic routing based on URL segments.
     ```jsx
     <Route path="/user/:id" component={User} />
     ```
   - **Programmatic navigation**
     - Allows navigation using code instead of links.
     ```jsx
     history.push('/home');
     ```

5. **Styling in React**
   - **Inline styles**
     - Styles can be added directly to elements using the `style` attribute.
     ```jsx
     const divStyle = { color: 'blue' };
     <div style={divStyle}>Hello World</div>
     ```
   - **CSS Modules**
     - CSS Modules allow scoped and modular CSS.
     ```css
     /* styles.module.css */
     .header { color: blue; }
     ```
     ```jsx
     import styles from './styles.module.css';
     <div className={styles.header}>Hello World</div>
     ```
   - **Styled-components**
     - Styled-components is a library for writing CSS in JavaScript.
     ```jsx
     import styled from 'styled-components';
     const Button = styled.button`
       background: blue;
     `;
     ```
   - **Emotion**
     - Emotion is another library for writing CSS in JavaScript, similar to styled-components.
     ```jsx
     import { css } from '@emotion/react';
     const buttonStyle = css`
       background: blue;
     `;
     ```

6. **Performance Optimization**
   - **useMemo, useCallback**
     - `useMemo` and `useCallback` are hooks that optimize performance by memoizing values and functions.
     ```jsx
     const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
     ```
   - **React.memo**
     - `React.memo` is a higher-order component that memoizes functional components.
     ```jsx
     const MemoizedComponent = React.memo(MyComponent);
     ```
   - **Code splitting**
     - Code splitting helps load parts of the application only when needed.
     ```jsx
     const OtherComponent = React.lazy(() => import('./OtherComponent'));
     ```
   - **Lazy loading and Suspense**
     - Lazy loading defers loading components until they are needed. `Suspense` is used to show a fallback while loading.
     ```jsx
     <Suspense fallback={<div>Loading...</div>}>
       <OtherComponent />
     </Suspense>
     ```

7. **Forms and Form Handling**
   - **Controlled vs Uncontrolled components**
     - Controlled components have their value managed by React, while uncontrolled components use refs to manage their value.
     ```jsx
     // Controlled
     <input value={value} onChange={handleChange} />
     
     // Uncontrolled
     <input ref={inputRef} />
     ```
   - **Handling form submissions**
     - Forms in React can be handled using event handlers.
     ```jsx
     function handleSubmit(event) {
       event.preventDefault();
     }
     ```
   - **Validation techniques**
     - Form validation can be done using various techniques like regex or validation libraries.
     ```jsx
     if (!email.includes('@')) {
       setError('Invalid email');
     }
     ```

8. **Testing in React**
   - **Jest and Enzyme**
     - Jest is a testing framework, and Enzyme is a testing utility for React.
     ```jsx
     expect(wrapper.find('button').text()).toBe('Submit');
     ```
   - **React Testing Library**
     - A testing library focused on testing React components.
     ```jsx
     const { getByText } = render(<Button />);
     expect(getByText('Submit')).toBeInTheDocument();
     ```
   - **Unit tests, integration tests, snapshot tests**
     - Unit tests test individual components, integration tests test interactions between components, and snapshot tests ensure UI doesn't change unexpectedly.
     ```jsx
     expect(renderer.create(<Button />).toJSON()).toMatchSnapshot();
     ```

9. **Server-Side Rendering (SSR)**
   - **What is SSR?**
     - SSR is rendering the initial HTML of a React component on the server, improving performance and SEO.
   - **Next.js basics**
     - Next.js is a React framework that supports SSR out of the box.
     ```jsx
     export async function getServerSideProps() {
       return { props: { data: await fetchData() } };
     }
     ```

10. **Common Patterns**
    - **Higher-Order Components (HOC)**
      - HOCs are functions that take a component and return a new component.
      ```jsx
      function withLogging(WrappedComponent) {
        return function(props) {
          console.log('Component rendered');
          return <WrappedComponent {...props} />;
        };
      }
      ```
    - **Render Props**
      - Render props is a pattern where a component's prop is a function that returns a React element.
      ```jsx
      <DataProvider render={data => <Component data={data} />} />
      ```
    - **Compound Components**
      - Compound components are a pattern where components work together to manage state and behavior.
      ```jsx
      function Modal({ children }) {
        return <div className="modal">{children}</div>;
      }

      Modal.Header = function Header({ children }) {
        return <div className="modal-header">{children}</div>;
      };
      ```

### Practical Topics

1. **Creating Components**
   - **Building functional and class components**
     - Functional components are simple functions, while class components are ES6 classes.
     ```jsx
     function Greeting() {
       return <h1>Hello!</h1>;
     }

     class Greeting extends React.Component {
       render() {
         return <h1>Hello!</h1>;
       }
     }
     ```
   - **Using Hooks in functional components**
     - Hooks like `useState` and `useEffect` add state and lifecycle methods to functional components.
     ```jsx
     const [count, setCount] = useState(0);
     useEffect(() => {
       document.title = `Count: ${count}`;
     }, [count]);
     ```
   - **Composing components**
     - Components can be composed to build complex UIs.
     ```jsx
     function App() {
       return (
         <div>
           <Header />
           <Content />
           <Footer />
         </div>
       );
     }
     ```

2. **State and Props Management**
   - **Managing component state**
     - State can be managed using `useState` in functional components or `this.setState` in class components.
     ```jsx
     const [state, setState] = useState(initialState);
     this.setState({ key: value });
     ```
   - **Passing props between components**
     - Props are passed from parent to child components.
     ```jsx
     <ChildComponent message="Hello" />
     ```
   - **Using Context for global state**
     - Context API is used for global state management.
     ```jsx
     const MyContext = React.createContext();
     ```

3. **Handling Events**
   - **Event handling in React**
     - Events in React are handled using camelCase syntax and passing functions.
     ```jsx
     <button onClick={handleClick}>Click me</button>
     ```
   - **Synthetic events vs native events**
     - React uses synthetic events to ensure compatibility across browsers.

4. **Conditional Rendering**
   - **Using conditional operators to render components**
     - Components can be conditionally rendered using ternary operators or logical AND.
     ```jsx
     {isLoggedIn ? <LogoutButton /> : <LoginButton />}
     ```
   - **Short-circuit evaluation**
     - Short-circuit evaluation can be used for conditional rendering.
     ```jsx
     {isLoggedIn && <LogoutButton />}
     ```

5. **List and Keys**
   - **Rendering lists using `.map()`**
     - Lists can be rendered using the `.map()` function.
     ```jsx
     const listItems = items.map(item => <li key={item.id}>{item.name}</li>);
     ```
   - **Understanding the importance of keys**
     - Keys help React identify which items have changed, improving performance.

6. **Side Effects**
   - **Using useEffect for data fetching**
     - `useEffect` is used for side effects like data fetching.
     ```jsx
     useEffect(() => {
       fetchData().then(data => setData(data));
     }, []);
     ```
   - **Cleanup in useEffect**
     - Cleanup functions can be returned from `useEffect` to run on component unmount.
     ```jsx
     useEffect(() => {
       const timer = setTimeout(() => setCount(0), 1000);
       return () => clearTimeout(timer);
     }, []);
     ```

7. **Routing**
   - **Setting up a Router**
     - React Router can be set up using `BrowserRouter`.
     ```jsx
     <BrowserRouter>
       <App />
     </BrowserRouter>
     ```
   - **Creating nested routes**
     - Nested routes allow defining routes within other routes.
     ```jsx
     <Route path="/user/:id" component={User} />
     ```
   - **Handling route parameters**
     - Route parameters can be accessed using `useParams`.
     ```jsx
     const { id } = useParams();
     ```

8. **Styling Components**
   - **Applying styles via CSS classes**
     - CSS classes can be applied using the `className` attribute.
     ```jsx
     <div className="container">Hello</div>
     ```
   - **Using styled-components for component-level styles**
     - Styled-components allow writing CSS directly in JavaScript.
     ```jsx
     const Button = styled.button`
       background: blue;
     `;
     ```

9. **Form Handling**
   - **Creating controlled and uncontrolled forms**
     - Controlled forms manage their state through React, while uncontrolled forms use refs.
     ```jsx
     // Controlled
     <input value={value} onChange={handleChange} />
     
     // Uncontrolled
     <input ref={inputRef} />
     ```
   - **Managing form state and validation**
     - Form state and validation can be managed using state hooks and validation libraries.
     ```jsx
     if (!email.includes('@')) {
       setError('Invalid email');
     }
     ```

10. **Data Fetching**
    - **Fetching data using `fetch` or Axios**
      - Data can be fetched using the `fetch` API or Axios.
      ```jsx
      useEffect(() => {
        fetch('https://api.example.com/data')
          .then(response => response.json())
          .then(data => setData(data));
      }, []);
      ```
    - **Using async/await with data fetching**
      - Async/await can simplify data fetching logic.
      ```jsx
      useEffect(() => {
        async function fetchData() {
          const response = await fetch('https://api.example.com/data');
          const data = await response.json();
          setData(data);
        }
        fetchData();
      }, []);
      ```
    - **Displaying data from APIs**
      - Fetched data can be displayed by setting it to the component's state.
      ```jsx
      return (
        <div>
          {data.map(item => (
            <div key={item.id}>{item.name}</div>
          ))}
        </div>
      );
      ```

11. **Debugging and Troubleshooting**
    - **Using React Developer Tools**
      - React Developer Tools is a browser extension that helps inspect React component hierarchies.
    - **Common debugging techniques in React**
      - Console logging, using breakpoints, and inspecting the component tree are common debugging techniques.

