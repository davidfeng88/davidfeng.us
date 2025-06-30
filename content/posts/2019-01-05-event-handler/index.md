---
title: 'React Component Event Handlers'
tags: ['React', 'tech', 'frontend']
date: 2019-01-05T12:11:48-05:00
aliases:
  - /posts/react/event-handler
---

Note: I published this article on [codeburst/Medium](https://codeburst.io/react-component-event-handling-660acb1cfd07) on 2017/07/30. It has received 18.3k views and 235 claps as of 2019/01/05.

---

What should be put in the `onClick={…}`?

<!--truncate-->

## A simple example: Toggle button

This example is from [React Docs](https://facebook.github.io/react/docs/handling-events.html), see it on codepen [here](https://codepen.io/gaearon/pen/xEmzGg).

In the `Toggle` class, a `handleClick` method is defined as an instance method, which changes the local state. In the `render` method, `this.handleClick` is passed to the `button` as an event handler. Finally, do not forget to bind `this` to `handleClick` in the constructor.

Note that in the `onClick={...}`, only the function name (`this.handleClick`) is passed in. **Do not invoke it**, i.e. do not write `onClick={this.handleClick()}`, since we do not want to change the state of a component while rendering it based on its state (more on that later). Also, this function has the synthetic event `e` as a parameter (the first line of this function is usually `e.preventDefault();`).

## A more sophisticated example: two modals

In [CollisionViz](https://collisionviz.davidfeng.us/), my recent web app which shows car crashes in NYC, I would like to have two buttons in my header, which open two modals respectively. To indicate which modal I want to show, in the state of the header component I created a `currentModal` field, whose value could be `""`, `"modal1"`, or `"modal2"` (I could have used a boolean if I have only one modal). In the skeleton below, what should `switchModal` do? How to pass it into the buttons’ `onClick` handler and the modals’ `closeModal` prop?

```jsx
import Modal from './Modal';

class Header extends React.Component {
  constructor(props) {
    super(props);

    this.state = { currentModal: "" };
    this.switchModal = this.switchModal.bind(this);
  }

  switchModal() {
    /* ??? */
  }

  render() {
    return (
      <header>
        <button onClick={...}>
          Open modal1
        </button>
        <button onClick={...}>
          Open modal2
        </button>

        <Modal
          show={this.state.currentModal === 'modal1'}
          closeModal={ /* ??? */ } >
          This is modal1
        </Modal>
        <Modal show={this.state.currentModal === 'modal2'}
          closeModal={ /* ??? */ } >
          This is modal2
        </Modal>
      </header>
    );
  }
}
```

### Step 1

1.1. Define three methods to set `currentModal` to `""`, `"modal1"`, or `"modal2"` respectively. Bind them to `this` in the constructor.

```js
closeModal(e) {
  e.preventDefault();
  this.setState({currentModal: ""});
}

showModal1(e) {
  e.preventDefault();
  this.setState({currentModal: "modal1"});
}

showModal2(e) {
  e.preventDefault();
  this.setState({currentModal: "modal2"});
}
```

1.2. Pass these methods to the buttons and the modals.

```jsx
<button onClick={this.showModal1}>
  Open modal1
</button>
<button onClick={this.showModal2}>
  Open modal2
</button>

<Modal
  show={this.state.currentModal === "modal1"}
  closeModal={this.closeModal} >
  This is modal1
</Modal>
<Modal
  show={this.state.currentModal === "modal2"}
  closeModal={this.closeModal} >
  This is modal2
</Modal>
```

This works. However, obviously the code is not [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). How can we improve?

### Step 2

2.1. Define a single `switchModal` method that takes a `modalName` parameter. Bind it to `this` in the constructor.

```js
switchModal(modalName) {
  this.setState({currentModal: modalName});
}
```

2.2. Pass the method with corresponding modal names to the buttons and the modals.

```jsx
<button onClick={this.switchModal("modal1")}>
  Open modal1
</button>
<button onClick={this.switchModal("modal2")}>
  Open modal2
</button>

<Modal
  show={this.state.currentModal === "modal1"}
  closeModal={this.switchModal("")} >
  This is modal1
</Modal>
<Modal
  show={this.state.currentModal === "modal2"}
  closeModal={this.switchModal("")} >
  This is modal2
</Modal>
```

This does not work. Why?

{{<figure src="./error.png">}}

Remember that we should not invoke the function we pass in? That’s exactly what we did here. How can we fix this?

### Step 3

Change the way we pass in the `switchModal` function in Step 2.2:

```jsx
<button onClick={ e => this.switchModal("modal1") }>
  Open modal1
</button>
<button onClick={ e => this.switchModal("modal2") }>
  Open modal2
</button>

<Modal
  show={this.state.currentModal === "modal1"}
  closeModal={ e => this.switchModal("") } >
  This is modal1
</Modal>
<Modal
  show={this.state.currentModal === "modal2"}
  closeModal={ e => this.switchModal("") } >
  This is modal2
</Modal>
```

This works. What’s happening here is that we passed a function in the form of `e => this.showModal(ModalName)` as event handlers without invoking `switchModal` function. Notice the event handler function has an `e` parameter, which is in line with the pattern in the previous `Toggle` example.

Can we make the code more DRY?

### Step 4

4.1. Change the `switchModal` method so that it returns an event handler function:

```js
switchModal(modalName) {
  return ( e => {
    e.preventDefault();
    this.setState({shownModal: modalName});
  });
}
```

4.2. Invoke `switchModal` with different parameters when passing it to the buttons and modals as event handlers, which looks exactly the same as what we did in 2.2. However, this time by invoking `switchModal`, we got the event handler back (without invoking it) as the return value.

```jsx
<button onClick={this.switchModal("modal1")}>
  Open modal1
</button>
<button onClick={this.switchModal("modal2")}>
  Open modal2
</button>

<Modal
  show={this.state.currentModal === "modal1"}
  closeModal={this.switchModal("")} >
  This is modal1
</Modal>
<Modal
  show={this.state.currentModal === "modal2"}
  closeModal={this.switchModal("")} >
  This is modal2
</Modal>
```

## Conclusions

An event handler function has a synthetic event parameter `e`, and it often has `e.preventDefault()` and changes the state of a React component. When writing event handlers for a React component, e.g.

```jsx
<Component onClick={...} ... />
```

Either write the event handler function’s name or invoke a function that returns an event handler function between the curly braces.
