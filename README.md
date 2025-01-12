# Map-Explorer-Web-Programming-Course-Final
[111-1] Web Programming Final

(Group 51) IM EEXPLORER

Demo Video Link
https://youtu.be/i1zdk_Maaag

Deployed Link
https://wpfinal-frontend.vercel.app

## How to deploy on localhost
1. GitHub clone `wp1111/final`, and pull down all file

#### Backend：
1. `cd backend`
2. create a `.env` file and include the following
MONGO_URL="YOUR_MONGODB_URL"
3. `yarn`
4. `yarn server`

#### Frontend：
1. `cd frontend`
2. create a `.env` file and include the following
REACT_APP_GOOGLE_MAPS_KEY="PLEASE_CREATE_YOUR_OWN_GOOGLE_MAP_KEY"
REACT_APP_BACKEND_URL=http://localhost:8080/
3. `yarn`
4. `yarn start`

## Web-Related Services and Testing Items

Services Provided by IM EEXPLORER:
IM EEXPLORER offers a platform with a user-friendly interface that allows users to easily record and share places they’ve visited using photos and text. Users can also view and search posts shared by others. On the My Map page, users can see all the places they’ve visited worldwide marked with pins. Clicking any pin on the map shows all the posts from that location, and users can view, edit, or delete individual posts.

Overview of IM EEXPLORER Features:
1. View and search all posts.
2. Register an account and log in.
(The following features require login)
3. Create, edit, and delete your posts.
4. The My Map page displays all the places you’ve visited and links to your posts in each location.

Detailed Testing Process for Each Feature:
### Searching Posts
The homepage initially displays all posts stored in MongoDB. Use the Search function to look for posts. After finding posts, click to view the Post Detail. Without logging in, you cannot perform Create Post, Edit, or Delete actions.

Search criteria can include:
1. Author (post creator),
2. Location (place tagged in the post),
3. Tags (post tags).
You can apply these filters individually or combine them.

Note:
Location is searchable via case-insensitive keyword matching (substring search).
Author and Tags require exact matches.
If a post and search query both include multiple tags, the post will appear as long as any tag in the post matches any tag in the query.

### Account Registration and Login
1. Logging in is required to perform Create, Edit, and Delete Post actions. When not logged in, clicking "Login" in the NavBar redirects you to the Login Page.
2. On the Login Page, users can log in. If an account doesn’t exist, click the Sign Up link at the bottom to go to the Sign Up page.
3. After successful registration, users are automatically redirected to the login page. Enter your credentials to log in.

Notes:
The Login and Sign Up pages include validation and error detection, displaying appropriate error messages.
Passwords are encrypted using bcrypt before being stored in the database.
Upon login, the backend sends a token for subsequent verification between the frontend and backend.

### Creating a Post
1. After logging in, click Create Post to add a new post.
2. Mark the desired location on Google Maps or enter a keyword in the search bar. Select a result from the dropdown or press Enter to mark the location.

Notes:
If the marked location corresponds to a landmark (not just an address), the Location field will automatically populate with the name of the landmark, and the address will display below the map (e.g., marking "National Taiwan University" will populate Location with "National Taiwan University" and Address with "No. 1, Section 4, Roosevelt Rd, Da’an District, Taipei City, Taiwan 106").
If the marked location is not a landmark, the Location field will not autofill the address to prevent excessively long names.

3. Users can manually edit the Location field.
4. Select the date of the visit using the Date Picker.
5. (Optional) Upload up to 10 images. If more than 10 images are uploaded, an error message will prompt  the user to remove excess photos.
6. (Optional) Add a Description and Hashtags.
7. Click Post and wait (photo uploads may take time). During this process, a loading screen is displayed. Once complete, the user is redirected to the homepage.

Notes:
To discard a draft, click Discard, and you will be redirected to the homepage.
The Create Post page includes validations to ensure Location, Date, and landmarks are filled.

### Homepage and My Post Features
1. Click Home Page to view all posts.
2. Click My Post to view all your posts.
3. Clicking a post displays its details. If it’s your post, you can Edit or Delete it.
4. Both the homepage and My Post pages support search functionality.

### Editing and Deleting Posts
If logged in, users can edit or delete their posts. Posts that do not belong to the user cannot be edited or deleted (the buttons won’t appear).

Note: Editing a post also takes some time, and a loading screen will appear. Upon completion, the user is redirected to the post.

### My Map Feature
1. After logging in, click My Map to display a world map with pins marking all the locations where posts have been made.
2. Clicking a pin shows all the posts made at that location on the right-hand side.
3. Clicking a post from the sidebar allows users to Create, Edit, or Delete posts as described above.

Note: The webpage layout is optimized for Mac.

## Frameworks/Modules/Source Code Used
- Frontend：axios, Geocoding API, Material-ui, Places API, React.js, react-google-maps, react-router-dom
- Backend：Amazon S3, Express.js, JWT, Mongoose, bcrypt
- SQL：MongoDB Atlas
- Deployment：Both frontend and backend are deployed using Vercel.
