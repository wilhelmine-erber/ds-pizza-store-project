# The Pizza Order store

Now the time has come, my friend....

You will now create the first source of your future income: Your own online store.

We gonna use functional components only with React hooks + Context API as our central data store.

In the backend we gonna use Express with MongoDB.

## Instructions

See a demo of the desired end result here:
[Pizza Store fullstack](https://pizza-store-two.vercel.app/)

Please develop this app in three stages / editions. See below...


## :3rd_place_medal: BASIC Edition - The Pizza List 

In this edition we wanna provide a basic page listing all pizzas available in our store.

As Bonus we might add some filtering...

The list of pizzas can initially be hardcoded in the frontend, but at the end should come from the API.

### DATA

This is how a pizza object might look like in the database / in Frontend Context state:

```
  _id: .....
  name: "Funghi",
  description: "Taste our Magic Mushrooms Pizza!",
  price: 5.99,
  image: "http://someserver.com/someimage.jpg
```

### BACKEND part

  * Setup a database "pizza_db" in Compass or ATLAS directly
  * Setup a basic backend with a home route
  * Create a pizza model
    * see the data spec above for a schema suggestion
  * Add a route /pizzas to get pizzas from the database
  * Create a seed script to store some pizzas there
  * Add CORS to allow accessing the pizzas route from your frontend

### FRONTEND part

  * Setup a Pizza Context & Provider
  * Provide a pizzas array centrally in Context for all components
  * Create some dummy pizzas				
  * Please create Two Components: PizzaList, PizzaItem
    * PizzaList should grab the items from context and render a list of PizzaItem components
    * PizzaItem should get passed the pizza data as prop and display the pizza data
  * BONUS: Add a search filter field to search pizzas by name part 
    * do NOT search pizzas at the API please, just in the frontend pizzas array only :)

### INTEGRATION:

  * Integrate the fetch call for getting pizzas


<br /><br />

## :2nd_place_medal: SILVER EDITION: Admin Page for Pizzas

In this edition we wanna allow full CRUD on our pizza store. 

### BACKEND part

  * Provide full CRUD routes in the API
  * Outsource Pizza related routes to own router
  * Test the routes with REST tool (e.g. Insomnia)

### FRONTEND part

  * Provide page /admin
  * Provide full CRUD against pizza array in Context
  * Ideally provide all CRUD on one page. Example: [Book App](https://book-app-rose.vercel.app)
  * BONUS: Allow inline editing. Example: [Book App](https://book-app-rose.vercel.app) (when double clicking an item)

### INTEGRATION

  * On every Pizza change in Context: Perform a PATCH / PUT request against the API too!
  * This way we keep the Context & the API in sync!
  * After a change in the frontend: 
    * Check if the change was created at the API too
    * Either start the API and call the /pizzas route or check the database entries in Compass / ATLAS

<br /><br />

## :trophy:	PLATINUM EDITION: The CART Page

Now we got hungry. Finally we wanna put some of these pizzas into a cart, so ideally some delivery person will ring our bell and we can stuff this super healthy stuff into our bodies...

### DATA

This is how a cart object might look like in the database / in Frontend Context state:

```
  _id: .....
  pizzas: [
    {  
      name: "Funghi",
      description: "Taste our Magic Mushrooms Pizza!",
      price: 5.99,
      image: "http://someserver.com/somefunghiimage.jpg
    },
    {  
      name: "Margherita",
      description: "Back to the basics!",
      price: 4.99,
      image: "http://someserver.com/somemargimage.jpg
    }
  ],
  createdAt: '2021-09-04',
  updatedAt: '2021-09-07'


```

So the "pizzas" field in the schema should be an array of pizzas!

You can allow an array field in your Mongoose schema using the "Array" datatype:

`  someField: Array `

This way you declare an array which can hold any JavaScript array data (no strict rules for its content)


### BACKEND part

  * Provide a "Cart" model
  * Provide a router for providing full CRUD against a cart (get all, create, edit, delete)
  * Test your routes with a REST client (e.g. Insomnia)
    * e.g. use the object above as BODY to see if a cart gets created / updated successfully

### FRONTEND part

  * Provide a cart object in your Context ` const [cart, setCart] = useState({...}) `
  * Initially the cart object should have NO id field
  * The cart object should contain a pizzas field holding an empty array

### INTEGRATION

  * Once the user clicks the "Buy" button on a pizza the first time					
    * create a Cart at the API
      * do so by sending over an cart object with an array of pizzas
      * store the returned cart, with its ID, in your Context
    * On every subsequent buy
      * UPDATE the cart object in state + make an UPDATE call (PATCH / PUT) to the Backend

<br /><br />

## General instructions

- Split up the team and code backend & frontend part in parallel
- Please use SEPARATE repositories for backend & frontend code!
- Ideally: Create an GitHub organisation and add all your teachers to it as members / collaborators
- Please use branches for coding & pull requests for integrating a new feature into the main branch

## Resources

### Fetch & State Updates

Wondering how to perform these freaky fetch calls against the API from React for GET, POST, PATCH/PUT, DELETE? And what to do with the results to keep central data (API) and local data (state) in sync?

Checkout the API connect guide with Fetch examples: https://github.com/losrobbos/api-connect-guide#using-fetch

### Gitty gitty...

Wondering how to do Git Branching & Merging in a team? 

Checkout this mini guide on the GitHub Flow method with concrete GIT commands for your branching workflow: https://github.com/losrobbos/github-flow-guide/blob/main/GIT_WORKFLOW.github.md