Summary: This application effectively demonstrates the capabilities of Express.js and EJS to create a simple yet functional blogging platform. With the enhancements made over the past few days, including improved routing, user interaction through post submissions, and responsive design with CSS, it provides a solid foundation for further development and feature expansion. 
Blogging Platform
Overview
This application is a simple blogging platform built using Express.js as the server framework and EJS as the templating engine for rendering dynamic HTML pages. The platform allows users to create, view, and manage blog posts, with separate pages for the home, about, and contact sections.

Key Components
1. Server Setup (app.js)
Dependencies: The application uses express, body-parser, ejs, and lodash.
Express handles routing and middleware.
body-parser parses incoming request bodies.
EJS renders views.
lodash helps with string manipulations (e.g., converting to lowercase).
Global Variables: An array called posts is declared globally to store the blog posts submitted by users.
Content Variables: Predefined content for the home, about, and contact pages is stored in separate variables (homeStartingContent, aboutContent, and contactContent).
2. Middleware Configuration
The application is set to use EJS as the view engine, and it serves static files from the public directory.
The body-parser middleware is configured to parse URL-encoded data, which is essential for processing form submissions.
3. Routing
Home Route (/): Renders the home page with the starting content and any posts submitted by users. The posts are displayed in a list format, with titles linking to their full content.
About and Contact Routes (/about, /contact): Render static content for the about and contact pages, respectively.
Compose Route (/compose): Displays a form for users to create new blog posts.
Post Submission Handling (POST /compose): When a user submits the form, the post is added to the posts array, and the user is redirected back to the home page.
4. Dynamic Post Viewing
Post Route (/posts/:postName): This route handles requests to view individual posts. It retrieves the requested post's title from the URL parameters, converts it to lowercase for case-insensitive matching, and checks if it exists in the posts array.
If the post is found, it renders a new EJS template displaying the full content of the post. If not, it logs 
NOT
FOUND! and renders a Page
Not
Found template.
5. EJS Templates
Home Template (home.ejs): Displays the home page with the predefined content and a list of posts. Each post shows a title and a truncated version of its content with a Read
more link.
Post Template: This template displays the full content of the selected post when a user clicks Read
more.
Not Found Template: Shows a friendly message if a user tries to access a post that doesn't exist.
Header and Footer Partials: Common UI elements like the header and footer are included in all pages using EJS partials.
6. Styling (CSS)
The CSS styles ensure that the layout is visually appealing and functional. It includes styles for the navbar, main content area, and footer.
The use of Flexbox helps in managing the layout, ensuring the footer remains at the bottom and does not overlap with the content regardless of how many posts are displayed.
Additional Features Implemented
Read More Links: Each post on the home page includes a Read
more link, allowing users to view the complete post.
Post Truncation: The content displayed on the home page is truncated to 100 characters with a ... indicating that more content is available.
Current Issues and Improvements
Routing Issues: If users encounter a not
found message when accessing certain posts (like day
1 or ma
pa
yin), it indicates that the URL parameters might not match the expected post titles due to case sensitivity or string matching issues. The routing logic can be improved to handle such cases better.
Footer Overlap: The footer was initially overlapping the content when multiple posts were displayed. This was resolved by adjusting the layout using Flexbox and ensuring the footer's position is relative.
