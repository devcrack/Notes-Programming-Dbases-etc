v-show
That directive only hides the element using css styles, but this still in the DOM, if we really want to remove from the page we should 
use the **v-if** directive. 

v-if
This remove the html from the page(from the DOM completly. 


## Directory Structure

- Public

    _In the public folder we can place assets such as images and font files and stuff like that, and any files we place in here will be available at the root of our app and everything you place in here will be easily available to all users. In this directory we have the index.html and here is where our app main view component will be mounted._

- src: 
    _Here is where we are going to be doing most of our work._
    
    _The main.js file this files is our app's main JavaScript file and this initializes the main VueJS required components._
    
    _The App.vue file is our main Vue component and this is where the layout of our app wil go. So all global componenets such as the header, the footer and the navigation drawer will go inside this file. In the content of this file we can find the **v-main** component and this is where all of the content of our app should be loaded, all the pages or views of our apps should be loaded within this component_

    Directories:
    - views
        
        _Is where all all of our views or pages will go._
    
    - assets

        _We can store images, fonts and stuff like that._
    
    - component:

        _Any child component of our views or our pages should be placed in here and we will be breaking up our pagers in child components and placing them in here._

    - plugins:

        _Any Vue.js plugin should go here like vuetify for example._

    - router:

        _In this file we can  manage all the pages and routes of our app._

    - store:
        _We have here an index.js file and such file we will configure our Vuex store._



