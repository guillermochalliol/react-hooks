# React Hooks

[Hooks](https://reactjs.org/docs/hooks-intro.html) are a new addition in React 16.8. They let you use state and other React features without writing a class.

In React, each component goes through different phases in its life, just as a person can go from being a student to a programmer, to later becoming an programmer. React components go through three phases: Mounting, Updating, and Unmounting.

The first phase, the **Mounting** phase, means that the component is in the process of inserting its content into the DOM.

The second, **Updating**, is called when the component is being updated. A component update occurs when there is a change in the state of the component or its props.

The next phase, the last one, is **Unmounting**, which is called when a component needs to be removed from the DOM.

 You can check a detailed documentation of Hooks on [Reacjs.org](https://reactjs.org/docs/hooks-overview.html)

### Below is a complete list of the most useful react hooks with their explanation:


<details open>
<summary><strong>State Hook</strong></summary>

This hook is to setup a State to our functional component 

useState() is a function that internally creates a variable where we can store the state of our component. It accepts an initial value and returns an array with two elements, the value and the function to modify it.

Since the value returned by the function is an array, we can break it down to access its elements individually.

`const [counter, setCounter] = useState(0);`
</details>
<details>
<summary><strong>Effect Hook</strong></summary>

It is the functional equivalent of **componentDidMount**, **componentDidUpdate**, and **componentWillUnmount** in class components.

The call to useEffect accepts a function as an argument. This function is executed by default when the component is first rendered, and then every time the component is rendered.

```
useEffect(()=>{
    console.log(counter)
});
```
It is also possible to specify when this function should be executed with an optional second argument that we can pass to it.

To do this, simply add a second parameter to the function, with the list of elements on which it depends, in this case the counter. If the value of the counter changes, the function will be executed with the next render. You can set multiple parameters to execute the useEffect hook

```
useEffect(()=>{
    console.log(counter)
}, [counter]);
```
Another possibility that this hook allows us is to specify that it be executed only once. This is very useful if we just want to make an API call to fill in the state of the application.

To do that only  add empty parameter array, this would tell React that our effect doesn't depend on any values, and therefore should only run on mount and unmount of our component.

If you're still thinking about classes, this means that our hook would become a **componentDidMount** and a **componentWillUnmount**.

```
useEffect(()=>{
    async function fetchCars(){
        const resp = await fetch(carsApiUrl);
        const cars = await res.json();
        setCars(cars)
    }
    fetchCars();
}, []);
```
The hook comes with a cleanup function, which you might not always need, but it can come in handy.

To invoke the cleanup function you can simply add a return function like so

```
useEffect(() => {
  let timer = setTimeout(() => setShow(true), 3000);
  return () => {
    clearTimeout(timer);
  };
}, []);
```
This will create a timeout in memory, so it would be best to clean this up.

The cleanup can prevent memory leaks and remove unwanted things. Some use-cases for this are:

- Clean up subscriptions
- Clean up modals
- Remove event listeners
- Clear timeouts
</details>