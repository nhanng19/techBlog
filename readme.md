# 14_Tech_Blog_NN
Model-View-Controller: Tech Blog

## The Challenge
Writing about tech can be just as important as making it. Developers spend plenty of time creating new applications and debugging existing codebases, but most developers also spend at least some of their time reading and writing about technical concepts, recent advancements, and new technologies. 
Our task is to build a CMS-style blog site similar to a Wordpress site, where developers can publish their blog posts and comment on other developers’ posts as well.

## Installation

Before running the application, create database by running the following commands in the MySQL shell (make sure navigation is in the root directory):

```bash
DROP DATABASE IF EXISTS techblog_db;
CREATE DATABASE techblog_db;
USE techblog_db;
```

Install node dependencies by running the following command (make sure navigation is in the root directory):

```bash
npm i
```

The application will be invoked by using the following command (make sure navigation is in the root directory):

```bash
npm start
```

Navigate in your browser to the following directory: 

```bash
localhost:3001
```

## User Story

```
AS A developer who writes about tech
I WANT a CMS-style blog site
SO THAT I can publish articles, blog posts, and my thoughts and opinions
```

## Acceptance Criteria

```
GIVEN a CMS-style blog site
WHEN I visit the site for the first time
THEN I am presented with the homepage, which includes existing blog posts if any have been posted; navigation links for the homepage and the dashboard; and the option to log in
WHEN I click on the homepage option
THEN I am taken to the homepage
WHEN I click on any other links in the navigation
THEN I am prompted to either sign up or sign in
WHEN I choose to sign up
THEN I am prompted to create a username and password
WHEN I click on the sign-up button
THEN my user credentials are saved and I am logged into the site
WHEN I revisit the site at a later time and choose to sign in
THEN I am prompted to enter my username and password
WHEN I am signed in to the site
THEN I see navigation links for the homepage, the dashboard, and the option to log out
WHEN I click on the homepage option in the navigation
THEN I am taken to the homepage and presented with existing blog posts that include the post title and the date created
WHEN I click on an existing blog post
THEN I am presented with the post title, contents, post creator’s username, and date created for that post and have the option to leave a comment
WHEN I enter a comment and click on the submit button while signed in
THEN the comment is saved and the post is updated to display the comment, the comment creator’s username, and the date created
WHEN I click on the dashboard option in the navigation
THEN I am taken to the dashboard and presented with any blog posts I have already created and the option to add a new blog post
WHEN I click on the button to add a new blog post
THEN I am prompted to enter both a title and contents for my blog post
WHEN I click on the button to create a new blog post
THEN the title and contents of my post are saved and I am taken back to an updated dashboard with my new blog post
WHEN I click on one of my existing posts in the dashboard
THEN I am able to delete or update my post and taken back to an updated dashboard
WHEN I click on the logout option in the navigation
THEN I am signed out of the site
WHEN I am idle on the site for more than a set time
THEN I am able to view comments but I am prompted to log in again before I can add, update, or delete comments

``` 

## The Process
To satisfy the criteria, we had to:
- Render client site with handlebar template engine
- Stylize the page with bootstrap
- Create association for Post, User, and Comments
- Set up API routes
- Create a database to store user's informations
- Create a user authentication with bCrypt

Specific functions of index.js:

Model Association
```javascript
Blogpost.belongsTo(User, {
  foreignKey: "user_id",
});

User.hasMany(Blogpost, {
  foreignKey: "user_id",
  onDelete: "CASCADE",
});

Comment.belongsTo(Blogpost, {
  foreignKey: "blogpost_id",
  as: "blogpost",
});

Comment.belongsTo(User, {
  foreignKey: "user_id",
  as: "user",
})

Blogpost.hasMany(Comment, {
  as: "comments",
});
```

## The Result
Users are able to view all blog posts on the landing page. Users can then log in or create an account to post blogs or comment on another blog. users can also view all the posts that they have made along with its respective comments.

## Submission
This project was uploaded to GitHub at the following repository link:
[https://github.com/nhanng19/techBlog](https://github.com/nhanng19/techBlog)

Deployed link:
[https://bloggingtech.herokuapp.com/](https://bloggingtech.herokuapp.com/)
