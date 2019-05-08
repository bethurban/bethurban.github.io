---
layout: post
title:      "Conditional rendering in React"
date:       2019-05-08 10:59:48 -0400
permalink:  conditional_rendering_in_react
---


For my final Flatiron School project using React-Redux, I decided to use the [Zillow API](https://www.zillow.com/howto/api/APIOverview.htm) to allow users to search addresses and get details on comparable properties to help inform real estate decisions. Users could also save addresses (called `homes` in the code) to bring up those searches again in the future.

While I was writing the code, I often came across instances where I needed to use conditional `if ... else` statements while rendering output from Zillow's API and the Rails API that I built to allow users to save homes.

## Inside JSX `return` statements

Inside JSX `return` statements, the [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) can be used in place of `if ... else`, which don't work in JSX.

Consider my `Homes` container from my project. When this container initially mounted, I wanted to check if a user was logged in. If so, the user would see a form (`HomeForm`) that would allow a new home to be saved, as well as each saved home's information via the `HomeCard` component.

If a user wasn't logged in, a simple message telling him or her to do so would display.

To accomplish the above, I used the ternary operator:

`condition ? true : false`

In that example, `condition` is evaluated. If found to be true, `true` is returned. If not, `false` is returned.

Here's how I used it in my `Homes` container (note that I removed JSX tags in this example such as `<div>` to make the ternary operation easier to see):

```
    return (
        { this.props.user ?
          <HomeForm />
					
          {this.props.homes.map(home =>
            <HomeCard home={home} user={this.props.user}  />
          )}
        :
          <h2>Please log in to save searches.</h2>
      }
    );
```

In the above `return` statement, the ternary operation is run inside curly brackets (`{}`).

First, the operation checks `this.props.user`. If a value returns, signaling that a user is logged in, the `HomeForm` container is returned. Then `map` is used to iterate over `this.props.homes` to return `HomeCard` components with each home's information.

If `this.props.user` does not return a value, meaning a user is not logged in, then all that will be returned is: `<h2>Please log in to save searches.</h2>`

## Outside JSX

React allows the use of the `if` operator in the same manner as JavaScript, as long as you're using it outside of your JSX `return` statements.

Consider my `Homes` container again. Once this container mounted, I wanted to call an async action (`getHomes`) along with the user's info in order to retrieve that user's saved homes from my Rails API. I only wanted to call the action if a user was logged in, so I used an `if` statement inside `componentDidMount` to check if a user had been saved in the props.

```
componentDidMount() {
    if (this.props.user) {
      this.props.getHomes(this.props.user)
    }
  }
```

If `this.props.user` returned a value, `getHomes` would execute and return the user's saved homes.


Further reading on conditional rendering in React that helped me as I built my project:

* [https://reactjs.org/docs/conditional-rendering.html](https://reactjs.org/docs/conditional-rendering.html)
* [https://react-cn.github.io/react/tips/if-else-in-JSX.html](https://react-cn.github.io/react/tips/if-else-in-JSX.html)
* [https://www.robinwieruch.de/conditional-rendering-react/](https://www.robinwieruch.de/conditional-rendering-react/)







