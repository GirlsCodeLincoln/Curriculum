# Unit 2 - Infrastructure as Code

## Overview
In this Unit we're going to build a whole software project as a random white elephant generator. THe

### Goals


### Lesson 1 - Build a feature list
Have the students write down the list of features they want on their website on a post it note. One note for each feature. After the students right down 3-4 ideas each put the ideas up on a board and group them up to similar groups of features. Then, group up the features and have the students (2 votes per student) vote for their favorite feature. They can use their votes however they want - all 2 on a single feature or split them to multiple.

Take this feature list and go over with the students the top 3 or so features, this is our MVP (minimum viable product) that will be built.

### Lesson 2 - Design a UI
Similar to lesson 1 have the students sketch out a UI that implements the features above. Post the pictures and have the students rank them using the 2 vote method. The highest getting feature 'wins' and will be the reference UI for the project. 

Discuss with the students this is how real life applications get built as well, as product owners rank the things important to them and decide collectively what to build.

### Lesson 3 - Design our Components
Before starting to build software we need to define the requirements and how our software is going to behave when interacting with the user. This is where we take the very high level idea we started making - the white elephant application with search, etc and start building out more detailed requirements as to what exactly it needs to do and how to do it. 

There are numerous terms for what this work is and how to do it, we'll be following a method called user stories which is usually associated with Agile software development.

- User Stories
    `As <who> <when> <where>, I <want> because <why>`
    `As a <role> I can <capability>, so that <receive benefit>`
    `As a [persona], I [want to], [so that].”`
- Acceptance Criteria
    Must be clear and establish pass/fail criteria.
    Unambiguous and Concise


### Exercise 3 - Build Acceptance Criteria for our components
Break up into 3 groups to cover the major pieces of functionality we need to build - Search, Sort, and Comment & Rate. For each component come up with the User Story and acceptance criteria.

As an example, all three of our components will need to retrieve their list of white elephant gifts from something we'll call the `Product Service`. My user story for the `Product Service` would look like this:

```
As a component developer I want to be able to query a list of products so that I can sort, filter, search, comment & rate them.
```

My acceptance criteria might look like

```
When I submit the query to the Product Service it must accept the query and the number of results to return.
If I submit a query to the Product Service it should respond with the product name, details, and a picture.
```

For each of our 3 components build the user story & acceptance criteria for the component.


### Lesson 4 -  Learning the Basics of Svelte
We're going to use [sveltejs](https://svelte.dev/) to build our webapp. It's a very simple front end library with a minimal set of concepts to learn designed for rapid web application builds. There are 7 main features we'll need to go over to understand how to build our components.

- Components
- Styling
- Reactivity
- Properties
- Events
- Templating
- Lifecycle

### Exercise 4 - Learning SvetleJS
In this exercise we're going to use a very basic SvelteJS application that returns a random catpicture when clicking a button. The component will also keep track of how many times we've clicked the button.


1. Open a new tab and browse over to the [svelteJS demo site](https://svelte.dev/repl/hello-world?version=3.13.0)
2. First lets add some styling to our application. Add this at the top of the left hand pane - the App.Svelte window. Feel free to change the color and font to whatever you want.
```
<style>
	.text {
		color: purple;
		font-family: 'Comic Sans MS';
		font-size: 2em;
	}
    .great {
        color: orange;
        font-family: verdana;
        font-size: 4em;
    }
</style>
```
3. Now, lets modify what the application says. The `<h1>` tag is bound to the variable `name`. Go ahead and change the value of `Your Name` to your real name.
4. Now lets apply some styling to our H1 tag - change the `<h1>` tag to read `<h1 class="great">`
5. We now can add our button that will handle retrieving our cat our dog picture. Add the following line right underneath our `<h1>` tag.
``` 
<button class="text" on:click={handleClick}>
	Retrieve Cat
</button>
```
6. We now need to add the eventHandler for our onclick. Add this inside the `<script>` block.
```
    let data = [];
	async function handleClick() {
        const response = await fetch("https://aws.random.cat/meow");
        const json = await response.json();
        data = json;
	}
```
7. Time for our template. We only want to display the picture if we get a cat obviously, so we're going to use some conditional logic here to only display the picture if `data.file` exists.
```
{#if data.file}
<img src={data.file} alt="Cat pictures please"/>
{/if}
```
8. Finally, lets add a counter for  how many cat pictures the people have view. add the following line to the top of your `script`

```
let count = 0;
```
9. Now, lets modify the `handleClick` function to increment the counter whenever it is called. Add the following line at the bottom of handleClick function - right above the `}`

```
count = count + 1;
```
10. Now lets output the data for the user. Add the following right below the button and right above your image - 
```
{#if count > 0}
<p class="purple">
	You've search for {count} kitties
</p>
{/if}
```

### Lesson 5 - Mapping our Features to the Framework
We now have our list of features and acceptance criteria as well as the framework (sveltejs). At this point as software developers we would start the process of designing the components themselves and how they'd work. Lets talk about 3 key ways software developers take the story cards and map them out to functionality in the frameworks they use

- flowchart
- data contracts

### Exercise 5 - Design our components
When building software it's very common to write out onto a paper how to design the system to work before actually building it. In this exercise we're going to try and decompose our component into smaller bits of functionality. In our case we have the 3 main bits of UI functionality

- Search
- Sort
- Comments & Rate

Break into 3 groups. In each of the three groups come up with the following:

1. What data your component needs to function. For example, if I  were writing the linking component - to link to the amazon results - I would need to know the URL to link to.
2. What data your component will need to modify if any. If, for example, we were building a linking component (to link to the white elephant results) our component wouldn't need to modify anything.
3. IF a user is going to interact with the component in any way - i.e. clicking on a button to do something - describe what that button click
4. Where possible describe the feature of SvelteJS you will use to finish the functionality.

