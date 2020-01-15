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

In the second sprint, our Trello board was updated to include the ability for all users (Admin, Volunteers, and Guests) to download images from the application. It was also discovered that the ability to search and browse image galleries/ categories for Administrators and Volunteers. This was amended. 

## Tech Stack
#### MongoDB
#### Express
#### React
#### Node


## Data flow diagram


## Wireframes


## Project Planning

<img src="./docs/Sprint_14Jan.png">
<img src="./docs/Sprint_15Jan.png">
<img src="./docs/MorningMeeting_15Jan.png">

From the outset our team agreed to implement the Agile methodology and to utilise tools that have proven to be industry favourites; GitHub, Trello, Jira, and Confluence. By creating a team repository on GitHub we could manage our version control as we all contributed to the project. Trello is a tool that we were familiar with. This was easy to set up initially, but we later opted to explore the Atlassian tools of Jira and Confluence. We are using Jira to manage our sprints and tickets. We have synced it with a Google Drive, GitHub, and Confluence. Our Confluence workspace is used for meeting notes  and managing rubric requirements. Again, it connects with our Google Drive for ease of access to documents before they are pushed to GitHub. 

Upon securing our client we set up an initial meeting to discuss the functionality of the proposed application. We walked through the general purpose, the ability to create, read, update, and delete data, and the authentication and authorisations that are needed. It was also established that we would engage in a minimum of weekly meetings to demonstrate our progress and to have feedback from the client. Or next meeting will be Monday 20 January. 
 
Equipped with detail meeting notes, we started day two with our first stand-up and sprint. For the documentation and planning stage of this project, we opted for daily stand-ups and sprints that would keep us on the same page while planning the functionality of the project. We delegate tasks, give each other feedback, and agree about what needs to be achieved each day. 

By implementing the Agile at the beginning of the project we were able to establish good communication practices and a collaborative team dynamic. As a result, we are ahead of the timeline on our documentation and are feeling like we have a solid base to begin our coding. 
