# MacArthur Museum Photo Management Application

### Rory Bell, Amber Emeny, Sarah Aldrich

## Purpose
The MacArthur Museum of Brisbane is a small museum with a large amount of historic image resources. Frequently, these assets are stored in file cabinets and can be hard to find. Currently, there is no tracking system and only a legacy understanding of gaps in the collection or the presence of duplicates. To enable research and the development of new exhibition/publication material the MacArthur museum has been on the hunt for an easy to use image management system. One challenge that always arose was cost. This MERN application aims to solve these problems and present the museum with a tool to upload, label, categorise and search their images at a negligible cost. 

## Functionality
The overall purpose of Archivise: the app is to **store photos and their relevant information / metadata**. Images and their metadata will be tied together so that users can know what they are looking at, but are also able to search and filter for the things images they need. 

To ensure that the application is used internally only, the landing page will prompt a user to sign in. The museum will set up at minimum three users to initiate the three different **roles** that will be built in the app: Admin, Volunteer, Guest. The Guest is intended for outside researchers and will be relegated to read only functionality. 

Admin will have the access to the full functionality of the app including **adding** users with roles, **editing** categories, and **deleting** both photos, categories, and users. Meanwhile Volunteers will be able to add photos and information, but will have no delete permissions. 

In relation to working with photos the app will utilise a form to submit the photo with the attached metadata and custom fields. This form will have an image upload section, a title for the museum cataloging number, a selection of categories that can be applied to an image, and a text area for free form information about the image to be entered. The fields relating to the categories and the textfield will be tied to specific metadata fields. This will tie the entered information directly to the digital image. Both an Admin and a Volunteer will be able to edit existing data as needed. To do so they will navigate to the image show page which will have an edit button. 

When conducting research, any user will have two means of **searching**. One option will be a text field where a user could type a key word. This would apply to user entered data pertaining to the historical context of an image. However, since humans are prone to error,  we need a secondary way to search. This will be done by a selecting menu that contains categories that are determined by the Admin user.  This will display "galleries" of all images with the applied tag. If a user was interested in downloading an image, they would be able to click a link that would initiate a full-sized image download from AWS.


## Target Audience
This application is largely designed for internal use by museum staff and volunteers. Using this tool they will be able to sort and manage their images and associated metadata. Currently, the MacArthur Museum digital image assets are stored on a hard drive and only people familiar with the past project can access them. They have been looking for a tool that is able to easily access their collection(s), add to the collection, edit the information present, sort the images, and search for specific topics. We aim to solve this challenge. 

Within the museum there are a variety of roles which will want different permissions and subsequently be targeted differently. 

The Executive Director and the Collection Manager want admin permissions. This will enable them to have access all CRUD operations. They want to be able to update and change category labels, add filters when needed, and delete errors when needed. They will need a simple interface that is easy to learn, use, and understand. 

One level below the admin will be the volunteers who help populate the database. Per the desires of the museum staff, volunteers will be able to upload images, add captions and apply categories. They will not have the ability to delete images or existing comments. Volunteers are a broad demographic ranging from those in high school or university to retirees that want to stay engaged. Again, we want the user experience to be self explanatory.

Lastly, the MacArthur museum wants the option to allow an outside researcher to log in and view their photos. The researcher will not have the ability manipulate the content, but simple be able to view, search, and filter the images. Their purpose is to learn more about a topic and access the related images. Provided that a research will likely only spend a few hours with the application, they need to quickly learn to use it and understand its options. 

## User Stories

<img src="./docs/Archivise-UserStories.png" />
<img src="./docs/Archivise-UserStories-2.png" />

In the second sprint, our Trello board was updated to include the ability for all users (Admin, Volunteers, and Guests) to download images from the application. It was also discovered that the ability to search and browse image galleries/ categories for Administrators and Volunteers. This was amended. 

---

## Tech Stack

This section of the documentation will cover the tech stack being used for the Archivise application. Included below are a Data FLow Diagram and an Application Architecture Diagram to aid in the explanation of the data flow and structure of the application from a technical perspective. Before delving into it each main element of the tech stack is explained below.

#### React

React is a front end javascript framework which is component-based and uses JSX which is a javascript XML language. Basically, it's a javascript embedded HTML. This allows the use of javascript for conditional rendering, of elements and components, and passing state data to components to control how and when they render and what data is available to them. React is what is used to develop the front end of a MERN stack application.

#### Node

Node JS is a runtime environment which allows javascript to be interpreted outside of a web browser. It is used to program the back end of a MERN stack application. The only shortfall of Node is that it is not designed to interact with HTTP methods which is why the express web framework was developed, which when stacked on top, enables us to build a fully scalable back end web server which, when connected with the REACT front end, creates the main structure of a MERN app.

#### Express

Express is a minimal and flexible Node.js web application framework that provides a robust set of features to develop web applications. It facilitates the rapid development of Node based Web applications. It aids heavily in building out the routes and server structure for the web app.

#### MongoDB

MongoDB is a document-based database which is a highly efficient, highly scalable, and open-source solution to storing data for a web application. The older more traditional Relational databases were not designed to cope with the scale and agility challenges that face modern applications, nor were they built to take advantage of the commodity storage and processing power available today. MongoDB tackles the challenges of the modern agile development environment and provides the data storage for a traditional MERN stack application.

#### AWS

AWS stands for Amazon Web Services. It is the cloud provider that will be used for physically storing the images. AWS is a large and widely used service and provides the "bucket" storage at a very reasonable price for scalable applications. It it is essential to use a suitable service like this for storing large databases of images to ensure application efficiency. The client will be set up on their own AWS account upon handing over the application to them.

### Axios

Axios is a client used heavily on the front end of the archvise application for making API requests to the back end server. Its responsible for fetching the data that is required for use in the front end returning a response usually containing the data that we need and automatically parsing a JSON response so it is immeditaley available for use. Axios is used in preference to the traditional fetch() syntax used in javascript as it is more effecient and a dryer solution within the code base. Client side support for protecting against XSRF is another out of the box convenience of uising the axios client.

---

**Application Architectural Diagram**

<img src="./docs/architecture-final.png">

---

The diagram above heavily depicts a MERN stack application. This is because it is indeed a MERN stack project. In the image above there are also some clients mentioned that are doing the work of connecting the front and back end of the application, as well as to the database and the cloud AWS Bucket. Below is a description of what each section of the application is doing.

Essentially the client will interact with the REACT app through their browser. React can do a fair bit on its own when no data needs to be persisted. It can use the components internal states which can be controlled with client-side functions and code to make an interactive UI for the user.

Once data is required whether it be for rendering to the screen or for use by a search parameter or any time that the user needs to interact in a way that manipulates the data that is stored in the database then REACT will use the integrated Axios client to make requests to the backend API of the application. Fetching the data it needs.

When the API receives a request from the front end of the application(REACT/AXIOS) the express web server will look for a defined route that matches the type of request that has been made. I.E POST, GET, PUT. This internal routing will then redirect to the appropriate controller which will do what is required with the data or fetch the required data interacting with the MongoDB Database. This is done using a client called Mongoose which enables us to model and validate the way we want our data stored. Mongoose also provides syntax to make queries to the MongoDB database and provides a configured connection to the mongoDB database. A response will then be sent back to the front end.

In our particular application we will store information that is needed to interact with the AWS client in MongoDB on the backend. The actual API calls and interaction with AWS will be done from REACT on the front end.

The application will be developed in an MVC architectural pattern. Meaning Model View Control.
The model references the data modelling of the application and takes care of any business logic associated with how the data should be stored. The view is everything visible to the client. The front end of the application that the client interacts with. The Controller is the middle man that takes care of fetching required data from the backend and sending it to the front-end(REACT).

The DFD below encapsulates the general flow of data from user interaction with the application.

---

![This is an image of the data flow diagram.](./docs/dfd-final.png)

---

### Deployment

**Back end**

The back end Node/Express server will be deployed on Heroku. Heroku is a well documented largely popular back end deployment service that is free of charge for basic sized applications. They provide excellent command-line tooling integration for developers for deployment ease.

Instead of hardware management, we deploy the app to Heroku, which packages the app’s code and dependencies into containers — lightweight, isolated environments that provide compute, memory, and OS, and filesystem. Containers are typically run on a shared host, yet are completely isolated from each other.

The Heroku Platform uses the container model to run and scale the app. The containers used at Heroku are called “dynos.” Dynos are isolated, virtualized Linux containers that are designed to execute code based on a user-specified command. Your app can scale to any specified number of dynos based on its resource demands.

**Front end**

The front end REACT segment of the app will be deployed on Netlify. Netlify is a popular and extremely easy to use deployment service for front end web applications. REACT with all of its complexity is only a static site upon deployment. This makes Netlify perfect for this purpose.

**Database**

MongoDB Atlas is a fully-managed cloud database developed by the same people that build MongoDB. Atlas handles all the complexity of deploying and managing your deployments on the cloud service.

---

## Wireframes

To save space in documentation, click the link here to view all wireframes: [https://github.com/Mern-A-team/MERN-assessment-documentation/tree/master/docs/Wireframes](https://github.com/Mern-A-team/MERN-assessment-documentation/tree/master/docs/Wireframes)

### Design

  The design for this application has been approached in an uncommon way. Typically most applications should follow mobile-first design, to ensure full responsiveness and functionality no matter the view port size. In the case of Archivise, where the audience is a specific group of people, the application will be used almost exclusively in desktop browsers. This means that functionality in a desktop view port size takes priority over the mobile sizes. Because of this, the application has instead followed desktop-first design practices.
     Desktop-first design meant choosing a left sidebar navigation over a typical responsive hamburger menu. While it may take up more space even in a collapsed state in mobile, this navigation style increases functionality on larger screens.

### User Flow

User flow for the web application is designed with the higher age demographic in mind. We wanted to provide a UI that is intuitive, easy to learn, and removes unnecessary clicks. The application is also designed to not allow the user past the landing page without logging in. This is to prevent the general public from accessing the archive.
![User Flow Diagram](https://raw.githubusercontent.com/Mern-A-team/MERN-assessment-documentation/master/docs/Wireframes/User-Flow%281%29.png)

#### User Flow Walkthrough

    - The user begins on the landing page where the only action is to click a log in button.
    - The log in form is rendered, the user can enter their details.
    - If the details are wrong, an invalid field error is displayed and a prompt is displayed to contact the administrator to reset the password.
    - Upon success, the user is taken to a dashboard that displays links relevant to the permissions of the User's role.
    - From this point, the User can access links from the left navbar, or directly from the dashboard.

##### Add Photo Link

 ==The *add photo* button only visible to Admin and Volunteers==

     - A form is rendered to add a new photo.
     - The User chooses the photo to upload, and the details to be associated with it.
     - If any details are invalid or the photo fails to upload, an invalid field error is displayed and a prompt is displayed to alert the User of the error.
     - Upon success, the new photo form is re-rendered and a thumbnail success alert is displayed, along with a link for the User to view the uploaded photo if they wish.
     - Note: this flow provides an easy process to upload multiple photos in succession.

##### Search Link

- A new page is rendered with a search bar and filters option.
- The "results gallery" initially shows all photos across all categories.
- The User can then select a category to add to the filters list, multiple times.
- After selecting search, the new gallery is rendered with all resulting images.
- From here, the user can select a photo to view details of.

###### View Photo Link

     - A new page is rendered that displays a high-resolution photo and its associated meta data, list of categories it belongs to and its description. 
     - At the end of the page there is an edit and delete button. 
     - If the user selects the **delete** button, a confirmation prompt is rendered, upon selecting "YES", the gallery results are displayed, and on selecting "NO" the view is redirected back to the show photo page.
     * ==The *delete* button only visible to Admin==
     - If the user selects the **edit** button, a new page with a form similar to the add photo form is rendered. For an invalid input or field, similar prompts to 'add photo' are displayed. Upon success or cancel, the view is redirected back to the show photo page.
     * ==The *edit* button only visible to Admin and Volunteers==

##### Categories Link

     - A new page is rendered that displays an indented list of all the created categories, each with an edit button beside it. 
     * ==The *edit* button only visible to Admin==
     - Here the user can select a category to view and upon click, the search gallery will be rendered with the relevant category filter readily applied. 
     - The **add category** link will display a prompt that yields a category name field and a drop down to select a parent category which allows the creation of   sub-categories.
     - ==The *add category* button only visible to Admin==
     - The **edit** link will render a form that allows the re-naming of a category and the deletion. By selecting **delete**, a confirmation prompt will appear. If the user selects no, they will be sent back to the category index page. If the user selects yes, the category will be removed, as well as all of it's sub-categories. The photos are not deleted, merely moved back into the "undefined" category. The user will then be redirected to an updated category index page.
     - ==The *edit* and *delete* buttons only visible to Admin==

##### Help Link

     - For a select few pages, selecting the help link will display a small window extending from the navbar with relevant instructions for operating the functions on the current page. Under the main heading there will also be a link that takes the user directly to the full website help documentation. However, for pages where specific instructions are not needed, only the link to the full documentation will be displayed.

##### User Management Link (Admin Only)

==Only visible to Admin==

     - When the "user management" link is clicked, the admin will be taken to a page that lists each user under the category of their assigned role. 
     - If the Admin clicks the **add user** link, a prompt is displayed with a username field, password field, a select field to assign the user's role, and information about each role and their associated permissions. Upon submission of the add user form, if there are any invalid fields, the appropriate errors are displayed, otherwise the updated User Management page is rendered with a confirmation alert.
     - If the Admin clicks on a specific user, an **edit user** prompt is displays which allows the admin to change the username, password, and role of the user. Upon a successful save, the updated user engagement page is rendered with the appropriate alert. On the edit user prompt, the admin also has the option to remove the user. If **delete** is selected, a confirmation prompt will appear. If the user selects no, they will be sent back to the user management page. If the user selects yes, the user will be removed, and the updated user management page will be rendered.

---

## Project Planning

<img src="./docs/Sprint_14Jan.png">
<img src="./docs/Sprint_15Jan.png">
<img src="./docs/MorningMeeting_15Jan.png">

From the outset our team agreed to implement the Agile methodology and to utilise tools that have proven to be industry favourites; GitHub, Trello, Jira, and Confluence. By creating a team repository on GitHub we could manage our version control as we all contributed to the project. Trello is a tool that we were familiar with. This was easy to set up initially, but we later opted to explore the Atlassian tools of Jira and Confluence. We are using Jira to manage our sprints and tickets. We have synced it with a Google Drive, GitHub, and Confluence. Our Confluence workspace is used for meeting notes  and managing rubric requirements. Again, it connects with our Google Drive for ease of access to documents before they are pushed to GitHub. 

Upon securing our client we set up an initial meeting to discuss the functionality of the proposed application. We walked through the general purpose, the ability to create, read, update, and delete data, and the authentication and authorisations that are needed. It was also established that we would engage in a minimum of weekly meetings to demonstrate our progress and to have feedback from the client. Or next meeting will be Monday 20 January. 
 
Equipped with detail meeting notes, we started day two with our first stand-up and sprint. For the documentation and planning stage of this project, we opted for daily stand-ups and sprints that would keep us on the same page while planning the functionality of the project. We delegate tasks, give each other feedback, and agree about what needs to be achieved each day. 

By implementing the Agile at the beginning of the project we were able to establish good communication practices and a collaborative team dynamic. As a result, we are ahead of the timeline on our documentation and are feeling like we have a solid base to begin our coding. 
