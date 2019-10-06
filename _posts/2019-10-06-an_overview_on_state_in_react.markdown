---
layout: post
title:      "An Overview of State in React"
date:       2019-10-06 12:23:00 -0400
permalink:  an_overview_on_state_in_react
---

**State** is a Javascript Object that stores dynamic data in a React class component. The state is initialized in the class constructor and is inserted into the component after **super(props)**. One of the many reasons that programmers use state is so you can create components that are both dynamic and interactive. **Properties or keys** can be added to the component's state with values. For example, in a signup component, a username and password could be the state keys as seen below.

```
class Signup extends Component {
  constructor(props) {
    super(props);
    this.state = {
      username: '',
      password: '',
    }
  }
```

React provides a method called **setState()**, which is used to change the update the component's initial state. An important rule to remember is that you cannot update state directly with:
```
this.state.attribute = "new value"
```

This is because it will not be able to direct the changes or trigger a re-render of the component. Instead, you should create a new object that is passed into this.setState() with the key-value pair. This will notify React that the component needs to be re-rendered with the new state. When the state successfully changes, the React component will re-render with the updated data.

Changing the state can also be utilized for **onClick** events. When a user clicks on a button that has access to one of the built functions, it will follow the actions that you provided in the component. In this example, I have created a function called incrementCounter, which includes this.setState() to increment the counter by 1.

```
incrementCounter = () => {
  this.setState({ counter: this.state.counter + 1})
}
```

When I click the button that's inside the return method of render, it will re-render with the new data incremented to the next value and return the new value of counter inside the h2 header. The button has access to the incrementCounter function because I attached to "this" and set it equal to onClick, an attribute of the button. This gives users the ability to transform data on the page in real-time.

```
  render() {
    return (
      <div>
        <button onClick={this.incrementCounter}>Increment Counter</button>
        <h2>{this.state.counter}</h2>
      </div>
    )
  }
```

Since state changes may occur asynchronously, you want to implement a callback as the second argument in the setState() method to access the newly updated state. You can then console.log the state to test and confirm that the state has been successfully updated.

```
this.setState( {username: 'alexz' }, () => console.log(this.state.username) ) ;
```

Another crucial rule of state is that updates are merged on the first level. When modifying one of the object keys, the other key-value pairs will remain the same. To update the key of another object inside the state, you need to insert a spread operator **...** so that the other keys and values are not overwritten.

```
this.setState(() => ({ 
  profile: { ...this.state.profile,
    name: "Alex"
    bio: "Full Stack Developer"
  }
 }
));
```

This is incredibly important for building a successful user interface because you do not want those using your application to lose personal information that they have already provided.



