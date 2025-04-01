How my code works
1) api_register.php - Edit: successful registration redirection
- If registration is successful ($stmt->execute) then we create a session and save the user id and redirects to the profileSetup page and returns a success notification.
Else returns an error message

2) logout.php - Created:
- if logout is clicked it unsets the session variables, destroys the session cookies, and the session, and redirects the user back to the login page

3) index.php - Edit: user post deletion success/failure messages
- if post is deleted the url will have posts.php?deleted=1 in it. If this is the case push a success message. If the url contains posts.php?error=1 then post a failure message

4) fitness_buddy.sql - Edit: payment table created
- this table stores user payment information

5) profileSetup.php - Edit: Added payment processing
- Line 104: Checks if user selected the premium membership option
- Line 106-110: Checks that all required fields are filled
- Line 119-120: Only displays the last 4 digits of the users entered credit card
- Line 123-134: Determines credit card type based on credit card criteria
- Line 136-160: Checks if payment info already exists and updates it to new info if entered. If no payment info exists inserts it instead.
- Line 433: The payment div class is hidden by default and will only show if premium is selected
- Line 557-583: A script that handles the payment display visiblity. If premium is selected the style is set to block and is visible. Otherwise its set to none just like default and invisible.
- Line 616-660: Validation which prevents payment from going through unless the credit cards is 13-16 numbers, the expiry date is a valid month and within 2020's, and cvc is either 3 or 4 digits long

5) myProfile.php - Created
- super simple form that fetches user profile information and displays it formatted

6) post.php - Created
- a post viewer that fetches the data from the table using the post creators id and displays it.

7) deletePost.php - Created
- checks if the user that wants to delete the post is the owner of the post and executes a delete query

8) editPost.php - Created
- checks if the post you want to edit exists, checks if the logged user is the owner, shows user a textarea, adds info using an insert query

9) forum.php - Edit: renamed, and added success and failure messages for deletion
- Like above if the url contains deleted=1 we post a success message. Else we post a fail message

Fitness Buddy
Fitness Buddy is a web application designed to help users stay connected and motivated on their fitness journey. The app features a user-friendly interface to create posts, interact with others, track fitness goals, and connect with fellow fitness enthusiasts. The app has a simple, Reddit-like interface for sharing fitness tips, progress, and motivation.

Features
  User Authentication: Users can register, log in, and manage their profiles.
  Post Creation: Users can create posts, share their fitness progress, or provide tips.
  Post Interaction: Users can view recent posts, including the poster's username and time of creation.
  No Posts Yet: If no posts exist, the user will be informed with a message saying "No posts yet :(".
  Post Viewing: Clicking on a post will allow users to view more details.

Pages
  Will add later
  
  Setup Instructions
  Requirements
  PHP 7.4 or higher
  MySQL Database
  XAMPP or equivalent local server environment
  
  Steps to Run the Application
  Clone the Repository

  Edit
  git clone https://github.com/anhad-dhiman/Fitness-Buddy.git


  Database Setup
    Create a database in MySQL named fitness_buddy.
    Import the provided SQL file to set up the necessary tables like users, posts, etc.
    Update Database Configuration

In the db.php file, ensure that the database connection details (username, password) are correctly set.
Start Your Local Server

Run your server using XAMPP or any other server software that supports PHP and MySQL.
Access the Application

Open a browser and navigate to http://localhost/fitnessBuddy to start using the app.
