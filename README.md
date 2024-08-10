[Link to codecademy lesson](https://www.codecademy.com/courses/react-101/lessons/the-state-hook/exercises/set-from-previous-state)


### The State Hook

**Set From Previous State**

In the previous exercise, we learned to update the state by passing it a new value like this:

setState(newStateValue);

However, React state updates are asynchronous. This means that there are some scenarios where portions of your code will run before the state is finished updating.

This is a good and a bad thing! Grouping the state updates together can improve performance in your application, but it can result in outdated state values. Consequently, it is best practice to update a state with a callback function, preventing accidental outdated values.

Let’s take a look at the following code to see how it’s done:

import React, { useState } from 'react';
 
export default function Counter() {
  const [count, setCount] = useState(0);
 
  const increment = () => setCount(prevCount => prevCount + 1);
 
  return (
    <div>
      <p>Wow, you've clicked that button: {count} times</p>
      <button onClick={increment}>Click here!</button>
    </div>
  );
}

When the button is pressed, the increment() event handler is called. Inside this function, we use our setCount() state setter with a callback function.

Because the next value of count depends on the previous value of count, we pass a callback function as the argument for setCount() instead of a value (as we’ve done in previous exercises).

setCount(prevCount => prevCount + 1)

When our state setter calls the callback function, this state setter callback function takes our previous count as an argument. The value returned by this state setter callback function is used as the next value of count (in this case, prevCount + 1).

We can also just call setCount(count +1) and it would work the same in this example, but for reasons that are out of scope for this lesson, it is safer to use the callback method.
