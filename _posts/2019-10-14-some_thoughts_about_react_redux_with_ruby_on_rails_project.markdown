---
layout: post
title:      "Some thoughts about React/Redux with Ruby on Rails Project"
date:       2019-10-14 04:02:26 +0000
permalink:  some_thoughts_about_react_redux_with_ruby_on_rails_project
---


It was a long journey to come to this point but finally I am working on my final project using React/Redux/Rails API. I created a web app that fetches the recipe data from external API, renders the result with React/Redux, and persists the data with Ruby on Rails.

Almost at the end of the project, I found one problem. In my web app, users can click "Like" button and write a review about their favorite recipe. And these favorite recipes are displayed in users own show page.

I thought everything was working fine but once I reset the date, I realized the page needed to be refreshed to render all the favorite recipes. It displays the past favorite recipes that are stored in rails API but it does not render a newly created favorite recipe in the users page.

After users click the submit, it goes through a fetch POST request and send the data to my rails backend API. The data is successfully posted but it can't be rendered when users goes to their page. But If users refresh the page, the data is displayed. So I need to refresh the page if I want to get the data I just created. But in our daily life, we won't refresh the page manually when we submit the form, right?? Somebody (my App) has to do it automatically. Hum, How can I this?


1. There is a method in plain Javascript
 `window.location.reload()`

According to MDN, >The Location.reload() method reloads the current URL, like the Refresh button.  ...   If true, the page is always reloaded from the server, bypassing the browser HTTP cache.

This sounds great for me. OK, it reloads the current URL. If we pass the argument `ture`, it reloads from the server. It means it fetches the data from rails.

This is what I understand.

So I put this method in the reducer. Just right after I posted user's review to rails, it will reload and users can get their favorites review and recipes from Redux state, which I already set up in advance. Also rails API has serializers, such as user `has_many :favorites` and `has_many :recipes` relationships so the reviews should be rendered.

But after I put `window.location.reload(true)`, the routes goes back to my home route.... That's not what I wanted. It is not good UI if it always go back to the home page whenever users submit the form. Users should remain at the same page.

The reload may be blocked, probably same-origin-policy or simply it is not a good idea. I'm trying to find out the solution but could not find it. The time is ticking and I need to finish my project...

So I decided to do another way.


2. Get the data from rails API
I confirmed the data was successfully posted to the rails API once users submit the reviews. So why can I just get the data again? Just post and get that data.

I know, I know.. sure, I can get the data. But I thought it might be an extra work compared to just refreshing the page. But anyway, I decided to do that.


My React App
`src/actions/userActions.js`

```
export const loadingUserInfo = (currentUserId) => {
    return (dispatch) => {
        return fetch(`http://localhost:3001/api/v1/users/${currentUserId}` ,{
            credentials: "include",
            method: "GET",
            headers: {
                "Content-Type": "application/json"
            },
        })
        .then(resp => resp.json())
        .then(userData => {
        dispatch(uploadingFavorite(userData.recipes))
        })
    }
}
```


Action creator
```
    return {
        type: 'UPLOADING_FAVORITE',
        payload: recipes
    }
}
```

User Reducer
```
export default (state = {
    recipes: []
}, action) => {
    switch(action.type) {
        case 'UPLOADING_FAVORITE':
            return {...state, recipes: action.payload}

        default:
            return state
    }
}
```


After I set up the above, user's favorite recipes were successfully stored in the state in my React app. So I can use and render this data in my User show page. But where can I call this function in my app? It is too late if I call this in the user's show page? It has to be called before rendered.

So `componentDidMount` works. componentDidMount() is invoked immediately after a component is mounted.


`src/containers/UserContainer.js`

```
class UserContainer extends Component {

    componentDidMount(){
        this.props.loadingUserInfo(this.props.currentUser.id)
    }

		.... do something
```

Right here, I am invoking `loadingUserInfo()` with arguments. My app can successfully get user's favorite recipes after mounted but before rendered. That means I can display the result (all users reviews) in User's page.

In React, it allows us to access that data we get the fetch call asynchronously. It happens very fast so it is important to keep in mind when and where the fetch is called and how and where we handle the data. It was hard to follow which part of data is rendered first but by placing debugger, redux dev tool, and adding console.log, finally I can see which function React is trying to call.

Official React component Lifecycle [cheat sheet](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/) also helps.
