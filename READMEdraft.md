# MacArthur Museum Photo Management Application

### Rory Bell, Amber Emeny, Sarah Aldrich

## Purpose
The MacArthur Museum of Brisbane is a small museum with a large amount of historic image resources. Frequently, these assets are stored in file cabinets and can be hard to find. Currently, there is no tracking system and only a legacy understanding of gaps in the collection or the presence of duplicates. To enable research and the development of new exhibition/publication material the MacArthur museum has been on the hunt for an easy to use image management system. One challenge that always arose was cost. This MERN application aims to solve these problems and present the museum with a tool to upload, label, categorise and search their images at a negligible cost. 

---

## Functionality
- store photos w/ relevant information
- update metadata
- search metadata 
- Download high quality images

We need a two-fold search/sort system. One piece will be user entered data  pertaining to the historical context of an image. However, humans are error prone, and we need a way to add filters to the photos that cannot be misspelled.  
	
---

## Target Audience
This application is largely designed for internal use by museum staff and volunteers. Using this tool they will be able to sort and manage their images and associated metadata. Currently, the MacArthur Museum digital image assets are stored on a hard drive and only people familiar with the past project can access them. They have been looking for a tool that is able to easily access their collection(s), add to the collection, edit the information present, sort the images, and search for specific topics. We aim to solve this challenge. 

Within the museum there are a variety of roles which will want different permissions and subsequently be targeted differently. 

The Executive Director and the Collection Manager want admin permissions. This will enable them to have access all CRUD operations. They want to be able to update and change category labels, add filters when needed, and delete errors when needed. They will need a simple interface that is easy to learn, use, and understand. 

One level below the admin will be the volunteers who help populate the database. Per the desires of the museum staff, volunteers will be able to upload images, add captions and apply categories. They will not have the ability to delete images or existing comments. Volunteers are a broad demographic ranging from those in high school or university to retirees that want to stay engaged. Again, we want the user experience to be self explanatory.

Lastly, the MacArthur museum wants the option to allow an outside researcher to log in and view their photos. The researcher will not have the ability manipulate the content, but simple be able to view, search, and filter the images. Their purpose is to learn more about a topic and access the related images. Provided that a research will likely only spend a few hours with the application, they need to quickly learn to use it and understand it's options. 

## User Stories
<img src="./docs/Archivise-UserStories.png" />

---

## Tech Stack

This section of the documentation will cover the tech stack being used for the Archivise application. Included below are a Data FLow Diagram and an application architecture diagram to aid in the explainatoin of the data flow and structure of the application from a technical perpective.

**Application Architectural Diagram**

<img src="Insert architecture diagram here when its fixed !!!">

The diagram above heavily depicts a MERN stack application. This is because it is indeed a MERN stack project. In The image above their are also some clients mentioned that are doing the work of connecting the front and back end of the application, aswell as to the database and the cloud AWS Bucket. Below is a description of what each section of the aplication is doing.

Essentially the client will interact with the REACT app through their browser. React can do a a fair bit on its own when no data needs to be persisted. It can use the componenets internal states which can be controlled with client side functions and code to make an interactive UI for the user. 

Once data is required weather it be for rendering to the screen or for use by a search parameter or any time that the user needs to interact in a way that manipulates the data that is stored in the datbase then REACT will use the integrated axios client to make requets to the backend API of the application. Fetching the data it needs.

When the API recieves a request from the front end of the application(REACT/AXIOS) the express web server will look for a defined route that matches the type of request that has been made. I.E POST, GET, PUT. This internal routing will then redirect to the appropriate controller which will do what is required with the data or fetch the required data interacting with the MongoDB Database. This is doen using a client called Mongoose which enables us to model and validate the way we want our data stored. Mongoose also provides syntax to make queries to the MongoDB database. A response will then be sent back to the front end.

In our particular application ALthough we will store required information that is needed to interact with the AWS client in MongoDB on the backend. The actual api calls and interaction with AWS will be done from react on the front end.

The application will be developed in an MVC architectural pattern. Meaning Model View Control.
The model references the data modelling of the application and takes care of any business login associated with how the data should be stored. The view is everything visible to the client. The front end of the application that the client interacts with. The Controller is the middle man that takes care of fetching required data from the backend and sending it to the front-end(REACT).


#### React

React is a front end javascript framework which is component based and uses JSX which is a javascript XML language. Basically it's a javascript emmbeded Javascript. This allows the use of javascript for conditional rendering, of elements and components, and passing state data to components to control how and when they render and what data is available to them. React is what is used to develop the font end of a MERN stack application.

#### Node

Node JS is runtime environment which allows javascript to be interpreted outside of a web browser. It is used to program the back end of a MERN stack application. The only short fall of Node is that it is not designed to interact with HTTP methods which is why the express web framework was developed, which when stacked on top, enables us to build a fully scalable back end web server which, when connected with the REACT front end, creates the main structure of a MERN app.

#### Express

Express is a minimal and flexible Node.js web application framework that provides a robust set of features to develop web applications. It facilitates the rapid development of Node based Web applications. It aids heavily in building out the routes and server structure for the web app.

#### MongoDB

MongoDB is a document based database which is a highly efficient, highly scalable, open souce and free solution to storing data for a web application. The older more traditional Relational databases were not designed to cope with the scale and agility challenges that face modern applications, nor were they built to take advantage of the commodity storage and processing power available today. MongoDB tackles the challenges of the modern agile developnment environment and provides the data storage for a traditional MERN stack application.

#### AWS

AWS stands for Amazon Web Services. It is the cloud provider that will be used for physically storing the images. AWS is a large and widley used service and provides the "bucket" storage at a very reasonable price for scalable applications. It it is essential to use a suitable service like this for storing large databases of images to ensure application efficiency. The client will be set up on their own AWS account upon handing over the application to them.

### Deployment

**Back end**

The back end Node/Express server will be deployed on Heroku. Heroku is a well documented largely popular back end deployment service that is free of charge for basic sized applications. They provide excellent command line tooling integration for developers for deployment ease. 

Instead of hardware management, we deploy the app to Heroku, which packages the app’s code and dependencies into containers — lightweight, isolated environments that provide compute, memory, an OS, and filesystem. Containers are typically run on a shared host, yet are completely isolated from each other.

The Heroku Platform uses the container model to run and scale the app. The containers used at Heroku are called “dynos.” Dynos are isolated, virtualized Linux containers that are designed to execute code based on a user-specified command. Your app can scale to any specified number of dynos based on its resource demands. 

**Front end**

The front end REACT segment of the app will be deployed on Netlify. Netlify is a popular and extremely easy to use deployment service for front end applications. REACT with all its complexity all in all is actually really only a static site upon deployment.

**Database**



## Data flow diagram

## Wireframes

## Trello
