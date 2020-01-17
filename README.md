# Archivise for MacArthur Museum of Brisbane

### Rory Bell, Amber Emeny, Sarah Aldrich

---

### contents
- Purpouse 
- Functionality
- Target Audience
- User Stories
- Tech Stack
- Deployment
- Third Party Packages
- Wireframes
- Project Planning
  

## Purpose

The MacArthur Museum of Brisbane is a small museum with a large amount of historic image resources. Frequently, these assets are stored in file cabinets and can be hard to find. Currently, there is no tracking system and only a legacy understanding of gaps in the collection or the presence of duplicates. To enable research and the development of new exhibition/publication material the MacArthur museum has been on the hunt for an easy to use image management system. One challenge that always arose was cost. This MERN application aims to solve these problems and present the museum with a tool to upload, label, categorise and search their images at a negligible cost.

  

## Functionality

The overall purpose of Archivise: the app is to **store photos and their relevant information / metadata**. Images and their metadata will be tied together so that users can know what they are looking at, but are also able to search and filter for the things images they need.

  

To ensure that the application is used internally only, the landing page will prompt a user to sign in. The museum will set up at minimum three users to initiate the three different **roles** that will be built in the app: Admin, Volunteer, Guest. The Guest is intended for outside researchers and will be relegated to read only functionality.

  

Admin will have the access to the full functionality of the app including **adding** users with roles, **editing** categories, and **deleting** both photos, categories, and users. Meanwhile Volunteers will be able to add photos and information, but will have no delete permissions.

  

In relation to working with photos the app will utilise a form to submit the photo w/home/roarkz/Code/projects/MERN-assessment-documentation/docs/MMB_13Jan.pngmage, and a text area for free form information about the image to be entered. The fields relating to the categories and the textfield will be tied to specific metadata fields. This will tie the entered information directly to the digital image. Both an Admin and a Volunteer will be able to edit existing data as needed. To do so they will navigate to the image show page which will have an edit button.

  

When conducting research, any user will have two means of **searching**. One option will be a text field where a user could type a key word. This would apply to user entered data pertaining to the historical context of an image. However, since humans are prone to error, we need a secondary way to search. This will be done by a selecting menu that contains categories that are determined by the Admin user. This will display "galleries" of all images with the applied tag. If a user was interested in downloading an image, they would be able to click a link that would initiate a full-sized image download from AWS.

  
  

## Target Audience

This application is largely designed for internal use by museum staff and volunteers. Using this tool they will be able to sort and manage their images and associated metadata. Currently, the MacArthur Museum digital image assets are stored on a hard drive and only people familiar with the past project can access them. They have been looking for a tool that is able to easily access their collection(s), add to the collection, edit the information present, sort the images, and search for specific topics. We aim to solve this challenge.

  

Within the museum there are a variety of roles which will want different permissions and subsequently be targeted differently.

  

The Executive Director and the Collection Manager want admin permissions. This will enable them to have access all CRUD operations. They want to be able to update and change category labels, add filters when needed, and delete errors when needed. They will need a simple interface that is easy to learn, use, and understand.

  

One level below the admin will be the volunteers who help populate the database. Per the desires of the museum staff, volunteers will be able to upload images, add captions and apply categories. They will not have the ability to delete images or existing comments. Volunteers are a broad demographic ranging from those in high school or university to retirees that want to stay engaged. Again, we want the user experience to be self explanatory.

  

Lastly, the MacArthur museum wants the option to allow an outside researcher to log in and view their photos. The researcher will not have the ability manipulate the content, but simple be able to view, search, and filter the images. Their purpose is to learn more about a topic and access the related images. Provided that a research will likely only spend a few hours with the application, they need to quickly learn to use it and understand its options.

  

## User Stories

  

<img  src="./docs/Archivise-UserStories.png" />

<img  src="./docs/Archivise-UserStories-2.png" />

  

In the second sprint, our Trello board was updated to include the ability for all users (Admin, Volunteers, and Guests) to download images from the application. It was also discovered that the ability to search and browse image galleries/ categories for Administrators and Volunteers. This was amended.

  

---

  

## Tech Stack

This section of the documentation will cover the tech stack being used for Archivise. Included below are a Data Flow Diagram and an Application Architecture Diagram. These figures aid in the explanation of the data flow and structure of the application from a technical perspective. Additionally, each element of the tech stack is explained below.

### React
React is a front end JavaScript framework which is component-based and uses JSX (a JavaScript XML language). Basically, it's a JavaScript embedded HTML. This allows the use of JavaScript for conditional rendering of elements and components as well as the ability to pass state data to components. This is used to control how and when they render and what data is available to them. React is what is used to develop the front end of a MERN stack application.

### Node
Node.js is a runtime environment which allows javascript to be interpreted outside of a web browser. It is used to program the back end of a MERN stack application. The only shortfall of Node is that it is not designed to interact with HTTP methods. For this reason the Express web framework was developed. When Express is stacked on top, it enables us to build a fully scalable back end web server. Subsequently, when connected with the REACT front end it creates the main structure of a MERN app.

### Express
Express is a minimal and flexible Node.js web application framework. It provides a robust set of features to which enable the rapid development of web applications. It aids heavily in building out the routes and server structure for the web app.

### MongoDB
MongoDB is a document-based database which is a highly efficient, highly scalable, and open-source solution to storing data for a web application. The older more traditional Relational databases were not designed to cope with the scale and agility challenges that face modern applications. Nor were they built to take advantage of the commodity storage and processing power available today. MongoDB tackles the challenges of the modern Agile development environment and provides the data storage for a traditional MERN stack application. In Archivise, MongoDB will be used to store the metadata for the images.

### AWS
AWS stands for Amazon Web Services. It is the cloud provider that will be used for physically storing the images in Archivise. AWS is a large and widely used service that provides "bucket" storage at a very reasonable price for scalable applications. It is essential to use a suitable service like this for storing large databases of images to ensure application efficiency. The client will be set up on their own AWS account upon handing over the application to them.

### Axios
Axios is an HTTP client used heavily on the front end of the Archivise application; specifically for making API requests to the back end server. It's responsible for fetching the data that is required for use in the front end and returning a response. The response usually contains data that we need and automatically parses a JSON response so it is immediately available for use. Axios is used in preference to the traditional fetch() JavaScript syntax, as it is more efficient and more DRY  within the code base. Client side support for protecting against XSRF is another convenience of using the Axios client.


---

  

#### Application Architectural Diagram

  

<img  src="./docs/architecture-final.png">

  

---

  

The diagram above depicts the architecture of a MERN stack application. It overviews the structure of the tools used to build Archivise. In the image above, there are clients that are doing the work of connecting the front and back end of the application, as well as to the database and the cloud AWS Bucket. Below is a description of what each section of the application is doing.

The client will interact with the **React** app through their browser. React can do a fair bit on its own when no data needs to be persisted. It can use the components internal states which can be controlled with client-side functions and code to make an interactive UI for the user.

Once data is required, whether it be for rendering to the screen, used in a search, or manipulated, React will use the integrated Axios client to make requests to the backend API of the application. It will fetch and act upon the specified data.

When the API receives a request from the front end of the application(React/Axios) the Express web server will look for a defined route that matches the type of request that has been made. For example: POST, GET,  & PUT. This internal routing will redirect to the appropriate controller. The controller will then do what is required with the data or fetch the required data interacting with the MongoDB Database. This is done using a client called Mongoose which enables us to model and validate the way we want our data stored. Mongoose also provides syntax to make queries to the MongoDB database and provides a configured connection to the MongoDB database. A response will then be sent back to the front end.

In Archivise the information that is needed to interact with the AWS client will be stored in MongoDB on the backend. The actual API calls and interaction with AWS will be done from React on the front end.

The application will be developed in an MVC architectural pattern. Meaning: Model, View, Controller. The Model references the data modelling of the application and takes care of any business logic associated with how the data should be stored. The View is everything visible to the client; the front end of the application that the client interacts with. The Controller is the middle man that takes care of fetching required data from the backend and sending it to the front-end(React).

  
The **Data Flow Diagram / DFD** below encapsulates the general flow of data from user interaction with the application.

---

  

![This is an image of the data flow diagram.](./docs/dfd-final.png)

  

---

## Deployment

####  Back end
The back end Node/Express server will be deployed on Heroku. Heroku is a well documented, largely popular back end deployment service that is free of charge for basic sized applications. They provide excellent command-line tooling integration for developers for deployment ease.

Instead of hardware management, we deploy the app to Heroku, which packages the app’s code and dependencies into containers — lightweight, isolated environments that provide compute, memory, and OS, and filesystem. Containers are typically run on a shared host, yet are completely isolated from each other.

The Heroku Platform uses the container model to run and scale the app. The containers used at Heroku are called “dynos.” Dynos are isolated, virtualised Linux containers that are designed to execute code based on a user-specified command. Your app can scale to any specified number of dynos based on its resource demands.

#### Front end
The front end React segment of the app will be deployed on Netlify. Netlify is a popular and extremely easy to use deployment service for front end web applications. React with all of its complexity, is only a static site upon deployment. This makes Netlify perfect for this purpose.

#### Database
MongoDB Atlas is a fully-managed cloud database developed by the same people that build MongoDB. Atlas handles all the complexity of deploying and managing your deployments on the cloud service.

---

## Third party packages (npm)

---


## Wireframes

  

---


## Project Planning

<img src="./docs/MMB_13Jan.png">

<img  src="./docs/Sprint_14Jan.png">

<img  src="./docs/Jira_roadmap.png">

<img  src="./docs/MorningMeeting_15Jan.png">


From the outset our team agreed to implement the Agile methodology and to utilise tools that have proven to be industry favourites; GitHub, Trello, Jira, and Confluence. By creating a team repository on GitHub we could manage our version control as we all contributed to the project. Trello is a tool that we were familiar with. This was easy to set up initially, but we later opted to explore the Atlassian tools of Jira and Confluence. We are using Jira to manage our sprints and tickets. We have synced it with a Google Drive, GitHub, and Confluence. Our Confluence workspace is used for meeting notes and managing rubric requirements. Again, it connects with our Google Drive for ease of access to documents before they are pushed to GitHub.

Upon securing our client we set up an initial meeting to discuss the functionality of the proposed application. We walked through the general purpose, the ability to create, read, update, and delete data, and the authentication and authorisations that are needed. It was also established that we would engage in a minimum of weekly meetings to demonstrate our progress and to have feedback from the client. Or next meeting will be Monday 20 January.

Equipped with detail meeting notes, we started day two with our first stand-up and sprint. For the documentation and planning stage of this project, we opted for daily stand-ups and sprints that would keep us on the same page while planning the functionality of the project. We delegate tasks, give each other feedback, and agree about what needs to be achieved each day.

By implementing the Agile at the beginning of the project we were able to establish good communication practices and a collaborative team dynamic. As a result, we are ahead of the timeline on our documentation and are feeling like we have a solid base to begin our coding.