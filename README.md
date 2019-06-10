# Vue.Js Fundamentals @ DevIntersection
DevIntersection 2019 (6/10/2019) - Vue.js fundamentals with Dan Wahlin and John Papa

## Description
Do you want to learn the fundamentals of Vue so you can start creating apps right away? Join us and you'll learn Vue from the ground up including how to display data, capture user interactions, create components, communicate across components, debug your app, add in plugins, and so much more.

### Goals
* Setup Your Environment with Essential Tooling
* Templating with directives, data rendering, methods, and computed properties
* Component Structure and Communication
* Create and Control Your App with the Vue CLI
* Navigating Your app with Routing
* Interact with APIs using Axios
* Manage State with Vuex

## Prerequisites
1. Install Node.js by [Downloading it here](https://nodejs.org/en/download/) & running through installer
2. Install Vue CLI via NPM  
`npm install -g @vue/cli`
3. Ensure that Vue CLI is in the path by going to command line and typing  
`vue --version`

# Understanding Vue

## Vue Components
Build greater things with them, similar to legos

A Vue Component can contain HTML, Styles, & Code (borrows principles from React & Angular)

Each component serves a single purpose on the page (Single Responsibility Principle in SOLID)

## Simplest Vue Application (01-First Vue App)
1. Get Vue from a CDN
2. Create some HTML
3. Create a Vue instance
4. Bind a model from the Vue instance to the HTML

## Vue CLI (02-Introduction to VueCLI)
```command line
vue create hue-vue -d
```
Vue CLI to create hello-vue application

```command line
vue run serve
```
Vue serve (host) the application

### Key Commands
* vue --help -> Help commands
* npm run lint -> Lint your code (fix)
* npm run build -> Build your app (Production Build with ES5 & ES6)
* npm run serve -> serve your app

## Important Vue Tooling (Optional)
* Node.js & NPM
* Vue CLI
* Visual Studio Code
* Browser tooling (Chrome Extension to dig and debug Vue)
* Ventur (Extension for Visual Studio Code)
* Vue Code snippets (Extension for Visual Studio Code)

### To Run CLI UI
```command line
vue ui
```
Runs an interactive User Interface for your Vue application

## Vue Syntax
### Global Registration (DO NOT USE)
// Global Registration
```javascript
Vue.component('component-a', { ... })
Vue.component('component-b', { ... })
Vue.component('component-c', { ... })
```

// Local registration
```javascript
var ComponentA = { /* ... */ }
var ComponentB = { /* ... */ }
var ComponentC = { /* ... */ }
```
### SFC (Single File Component) (USE THIS)
```javascript
import ComponentA from './ComponentA.vue'

export default {
 components: {
   ComponentA
 },
 // ...
}
```


# Resources

### John Papa
* https://johnpapa.net
* Twitter: @John_Papa
### Dan Wahlin
* https://codewithdan.com
* Twitter: @DanWahlin

### Get the Content
* [Slides](https://jpapa.me/vue-1-day])
* [Labs](https://jpapa-me/vuelabs)
* [Setup](https://jpapa.me/vueworkshopgist)