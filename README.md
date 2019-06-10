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

## [Simplest Vue Application](https://github.com/ZinkNotTheMetal/VueJsFundamentals/tree/master/01-First%20Vue%20App)
1. Get Vue from a CDN
2. Create some HTML
3. Create a Vue instance
4. Bind a model from the Vue instance to the HTML

## [Introduction to the Vue CLI](https://github.com/ZinkNotTheMetal/VueJsFundamentals/tree/master/02-Introduction%20to%20VueCLI/hello-world)
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
```javascript
// Global Registration
Vue.component('component-a', { /* ... */ })
Vue.component('component-b', { /* ... */ })
Vue.component('component-c', { /* ... */ })
```

```javascript
// Local registration
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

## Displaying Data and Binding
| Syntax | Description |
|:-------|:----------- |
| `{{ propertyName }}` | Bind to and display property value |
| `{{ 2 + 2 }`} | Template Expression (BE CAREFUL to use, prefer computed property) |
| `v-bind:href="model"` | Property Binding (href) - defined in data() |
| `v-on:click="statement"` | Event binding |
| `v-model="model"` | Two-way binding |
| `v-once` | Display a value once, but not see any updates (mainly used for efficiency) 

Property Binding - (:) to get rid of binding 
```html
<a :href="url"></a>
.special { font-weight:bold; }
<span :class="{special: name === 'John'"></span>
```

## Event Bindings (DOM bindings)
Event bindings execute an expression when an event occurs
v-on:event="expression" but shortcut is @event="expression"
```html
<button @click="reset()">Reset</button>

<script>
export default {
    data() { ... },
    methods: {
        reset() {
            this.name = "Madelyn";
        }
    }
}
</script>
```

## Display a List
Iterate over a list of items in a model. Identify a unique key, for faster rending
```html
<ul>
    <!-- :key helps Vue with modifications on the unique identifier on the row (optional) -->
    <li v-for="hero in heros" :key="hero.id">
        {{ hero.name }}
    </li>
</ul>
```

## Conditionals
Display content based on an expression (add/remove from the DOM)
```html
<div v-if="selectedHero">
    You selected {{ selectedHero.name }}
</div>
```

## Combined Lists and Conditionals
```html
<ul>
    <li
        v-for="hero in heros"
        :key="hero.id"
        @click="selectedHero=hero"
        :class="{highlight: selectedHero === hero}">
    {{ hero.name }}
    </li>
</ul>
<div v-if="selectedHero">
    You selected a hero who is {{ selectedHero.name }}
</div>
<script>
    ...
    data() {
        return {
            selectedHero: undefined,
            heros: [
                { id: 10, name: 'Ella' },
                { id: 20, name: 'Madelyn' },
                { id: 30, name: 'Haley' }
            ]
        }
    }
<script>
```

## What about only visibility
Does not have to do as much DOM manipulation, just uses hidden and classes in the background
```html
<div v-show="selectedHero">You selected a hero</div>
```
## Interacting with a Component
### The data() function
* Models for the component
* Defines an object for the model
* Vue creates getters/setters for each property
* Recommended
  * A function that returns the initial data object
  * New component instances won't share state


### [Lifecycle Hooks](https://vuejs.org/v2/api/#Options-Lifecycle-Hooks)
* beforeCreate -> before the element has even been created (not many people use this)
* created -> not on the DOM yet (good time to get Data kick off async calls)
* beforeMounted
* mounted -> another time to get data (DOM is available - good for 3rd party libraries)
* beforeUpdate
* updated -> similar to onChanges
* beforeDestroy
* destroyed

Read the Vue docs for more information

## [Computed Properties](https://vuejs.org/v2/guide/computed.html#Computed-Properties)
* Fire when any dependency value changes
* Cached based on its **reactive dependencies**
* Will only re-evaluate when some of its reactive dependencies have changed

```javascript
computed: {
    fullName() {
        return `${this.selectedHero.firstName} ${this.selectedHero.lastName}`;
    },
    reversedName() {
        return (this.name = [...this.name].reverse().join(''));
    }
}
```

### [Computed get/set](https://vuejs.org/v2/guide/computed.html#Computed-Setter)
Computed properties support getter and setter functions
```javascript
computed: {
    fullName: {
        get() {
            let value = this.first;
            value += this.last ? ` ${this.last}` : ""
            return value;
        },
        set(value) {
            var names = value.split(" ");
            this.first = names[0];
            this.last = names.length === 1 ? "" : names[names.length - 1];
        }
    }
}
```

### [Watchers](https://vuejs.org/v2/guide/computed.html#Watchers)
* React to data changes
* Named same as reactive value
* Accepts new and old values
* Ideal for asynchronous operations

```javascript
watch: {
    hero(newHero, oldHero) {
        console.log(newHero.name);
        console.log(oldHero.name);
    }
}
```

### Filters
Usable with {{ }} interpolations and v-bind expressions
```javascript
filters: {
    capitalize(value) {
        if(!val) return ''
        value = value.toString()
        return value.charAt(0).toUpperCase() + value.slice(1)
    }
}
```
Template
```html
<div>
    Hello {{ name | capitalize }}
</div>
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