---
title: 'Clean Code in React'
date: 2019-01-05T13:07:44-05:00
aliases:
  - /posts/react/clean-code
tags: ['React', 'clean code', 'Bara']
---

I published this article on [codeburst/Medium](https://codeburst.io/clean-code-in-react-fe11372f331c) on 2018/01/28. It has received 12.6k views and 1.96k claps as of 2019/01/05.

---

My first full stack project is [Bara](https://bara.davidfeng.us/#/), a single-page Yelp clone. After weeks of development and refactoring, I am pretty happy with the result. The UI looks good; the functionality works fine: users can sign up, log in, CRUD businesses and reviews.

<!--truncate-->

{{<figure src="./bara-home.png">}}

Recently I’ve been reading [Clean Code](https://amzn.to/2L0MAka), and I begin to appreciate the importance of keeping the code clean. Programmers are authors; the code is like books we write, except our reader almost never begin to read from page 1. Usually the reader directly dives into a module/component to fix a problem or add a feature. To help the reader (could be your teammate, or even future you!), it is the author’s responsibility to make sure that the code is easy to read (and to change, but that’s another big topic). Martin Fowler said:

> Any fool can write code that a computer can understand. Good programmers write code that humans can understand.

I decided to refactor Bara as a practice. The code works (the computer understands it), but it’s not clean. I did not intentionally make my code hard to read; (at least I took care of indentations and whitespace) but that code was far from clean. For example, the `Home` component, which renders the homepage, looked like this:

```jsx
import React from 'react';
import { fetchFeaturedBusinesses } from '../../util/business_api_util';

import HomeBarContainer from './home_bar_container';
import SearchBar from '../header/search_bar';
import HomeLinks from './home_links';
import { FeaturedBusinesses, Categories } from './home_util';

export default class Home extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      defaultBackground: true,
      loading: true,
      businesses: [],
    };

    this.handleClick = this.handleClick.bind(this);
  }

  componentDidMount() {
    this.handleClick();
  }

  handleClick() {
    fetchFeaturedBusinesses().then((businesses) => {
      this.setState((prevState) => ({
        loading: false,
        businesses,
        defaultBackground: !prevState.defaultBackground,
      }));
    });
  }

  homeHero() {
    let homeHeroContent = (
      <div>
        <HomeBarContainer />
        <div className="logo" onClick={this.handleClick}>
          <img src={window.staticImages.homeLogo} />
        </div>
        <div className="home-search">
          <SearchBar />
        </div>
        <HomeLinks />
      </div>
    );
    return (
      <div
        className={
          this.state.defaultBackground ? 'home-header-1' : 'home-header-2'
        }
      >
        {homeHeroContent}
      </div>
    );
  }

  featuredBusinesses() {
    return this.state.loading ? (
      <img className="spinner" src={window.staticImages.spinner} />
    ) : (
      <FeaturedBusinesses businesses={this.state.businesses} />
    );
  }

  render() {
    return (
      <div>
        {this.homeHero()}
        <div className="center">{this.featuredBusinesses()}</div>
        <Categories />
      </div>
    );
  }
}
```

The `Home` component has three parts. From top to bottom, they are: 1. `HomeHero`, which contains the `HomeBarContainer` (login and sign up links), the logo, the `SearchBar`, and `HomeLinks`; 2. `FeaturedBusinesses`, which is just three random businesses; 3. `Categories`, which contains links to different businesses based on their categories. The core functionality of this page is that clicking on the logo changes `FeaturedBusinesses` and the background image of `HomeHero`.

---

However, if my code were cleaner, not a single word in the previous paragraph would be necessary. The code can (and should) tell you what it does, explicitly, in a human-friendly way.

```jsx
import React from 'react';
import PropTypes from 'prop-types';
import HomeHero from './HomeHero';
import FeaturedBusinesses from './FeaturedBusinesses';
import Categories from './Categories';

const Home = ({
  handleHomeLogoClick,
  hasDefaultBackground,
  featuredBusinesses,
  isLoading,
}) => (
  <div>
    <HomeHero
      handleHomeLogoClick={handleHomeLogoClick}
      hasDefaultBackground={hasDefaultBackground}
    />
    <FeaturedBusinesses
      featuredBusinesses={featuredBusinesses}
      isLoading={isLoading}
    />
    <Categories />
  </div>
);

export default Home;

Home.propTypes = {
  handleHomeLogoClick: PropTypes.func.isRequired,
  hasDefaultBackground: PropTypes.bool.isRequired,
  featuredBusinesses: PropTypes.arrayOf(PropTypes.object).isRequired,
  isLoading: PropTypes.bool.isRequired,
};
```

Here’s what I did to make the code cleaner (a lot of these came from feedbacks after I published my post on Medium, especially [suggestions from Fanis Despoudis](https://medium.com/@fanisdespoudis/hey-you-can-go-even-further-6d454def95f)):

## Split the container and presentational components

Now I have two components: `HomeContainer` and `Home`. This is the paradigm recommended by [Dan Abramov](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0). The container component handles all the logic, while the presentational component handles the display only. You have more files, but each file is smaller, thus easier to understand. Sometimes I felt the logic is straightforward enough that I don't really want to split them up, but splitting almost always produces better code.

## ESLint is your friend

You may have noticed that I changed the file names to uppercase H, and the `Home` component is validating its props with [prop-types](https://www.npmjs.com/package/prop-types). These suggestions all came from ESLint. I used [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb), and it told me when to use single quotes and double quotes; how to improve the accessibility of my components (adding alt text to images is a good start but there is so much more) ... The list goes on and on. Get rid of those ESLint errors and warnings, not only your code will be infinitely better, but also you’ll learn a ton in the process.

## Handle binding gracefully with arrow function in class property

In React, usually you need to `bind` the event handler to handle `this` properly. Apparently there are at least [five ways to do it](https://medium.freecodecamp.org/react-binding-patterns-5-approaches-for-handling-this-92c651b5af56), but the easiest is to use arrow function in class property. I was using Babel 6, thus I needed [babel-plugin-transform-class-properties](https://www.npmjs.com/package/babel-plugin-transform-class-properties). Since I don’t need to bind my event handlers in the component’s constructor anymore, suddenly **I don’t even need the constructor itself**. All I need to do is to initialize my state like this:

```jsx
state = {
  hasDefaultBackground: true,
  isLoading: true,
  featuredBusinesses: [],
};
```

## Break down the component: only one level of abstraction per component

The `render` method returns the three sub-components: `HomeHero`, `FeaturedBusinesses`, and `Categories`.

Initially I only created `Categories` component since it’s static, while `HomeHero` has a `handleClick` callback, and `FeaturedBusinesses` has some extra logic. However, I can pass those information to the children as props, and this greatly cleans up the `render` method. The `Home` component does not have to know `SearchBar` or `HomeBarContainer`, let `HomeHero` take care of those.

## Break down the function: only one level of abstraction per function

For example, the original `handleClick` does several things: it fetches featured businesses from the backend, saves them in the local state, and changes the background of `HomeHero`.

I group the first two things together since there is a logic connection between them, while changing the background is a totally separate issue. Therefore in the new `handleHomeLogoClick` function, I call two functions to take care of each of them: 1. fetch and save featured functions; 2. update `HomeHero`'s background. Of course the first function can be further broken down.

The one level of abstraction rule gives the reader an option to ignore implementation details if he/she does not care. Overall, the logic is much more explicit, making the code less error-prone. Actually, after this refactoring, I found that in my old version of `componentDidMount`, I shouldn’t update `HomeHero`'s background. In the new structure this bug becomes pretty obvious.

## Use more descriptive names

The functions I mentioned in last section were named as `fetchAndSaveFeaturedBusinesses`, `saveFeaturedBusinesses`, `updateHomeHeroBackground`, etc. Moreover, in the local state, `businesses` field was renamed to `featuredBusinesses`, and `handleClick` function was renamed to `handleHomeLogoClick`. The extra information makes the code easier to understand (for humans!).

## Conclusion

Write clean code. Your teammate and future you will thank you later. If you find this post interesting, make sure to check out [Clean Code by Uncle Bob](https://amzn.to/2C7jagz). [Clean Code vs. Dirty Code: React Best Practices](https://americanexpress.io/clean-code-dirty-code/) is also helpful.
