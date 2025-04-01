How my code works
1) api_register.php - Edit: successful registration redirection
- If registration is successful ($stmt->execute) then we create a session and save the user id and redirects to the profileSetup page and returns a success notification.
Else returns an error message

2) logout.php - Created:
- if logout is clicked it unsets the session variables, destroys the session cookies, and the session, and redirects the user back to the login page

3) index.php - Edit: user post deletion success/failure messages
- if post is deleted the url will have posts.php?deleted=1 in it. If this is the case push a success message. If the url contains posts.php?error=1 then post a failure message

4) fitness_buddy.sql - Edit: created 2 tables
- Payment Table: this table stores user payment information
- Match Request Table: holds records on match requests and uses them to allow users to request, accept, and deny requests. Also sets a pending state for a request

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

10) matches.php
- Updated the Nav bar of all pages to properly redirect to matches.php
- added a match_request table
- uses a complicated sql statement which
  - L23-L36: collects user information and profile details from the users table and user_profiles table
  - L37-L43: uses the if statements (CASE) in SQL to see if the profile details match and gives a score which adds together to potentially total 100
  - L37-L43: This score is saved as a variable which is used to show the user how "compatible" the user is
  - Inner Join used between users and user_profiles
  - Left Join used to obtain more information on match requests
  - L52: Excludes the current user, a user you've sent a match request to, or the user who sent you a match request from the list of available users you can send requests to. Basically, you can't send a request to someone who you're already matched with or having a pending match request with.
  - L56: note: 'remove AND (mr.status = 'pending' OR mr.status = 'accepted')' to prevent rejected users from being listed. This exists for testing purposes
- L64-85: just extracts data and binds it to php variables
- L87-97: retreives the requests the user sent - displayed in html
- L103-112: retreives the requests the user received - displayed in html
- L117-139: formats the data like myProfile.php
- 141-173: Checks if a request exists and if it doesn't inserts a pending status match request row
- 175-229: Original code is commented out
  - Commented Original Code: Sets status based on if it was accepted or declined
  - New Code: If accepted changes status to accept. If denied straight up deletes it so we can test the matching feature with 2 users only.


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
