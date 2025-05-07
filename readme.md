# Facebook Page Poster

A simple application to post messages and media (images/videos) to one or more Facebook Pages you manage.

## Features

*   Post text messages.
*   Upload and post single images or multiple images.
*   Upload and post single videos.
*   Post to multiple Facebook Pages simultaneously.
*   User-friendly interface with status feedback.

## Note
This will not work if hosted because 
Facebook blocks many client-side Graph API calls for actions like posting to pages due to privacy, rate-limiting, and token abuse risks.

You’ll likely hit CORS errors when calling https://graph.facebook.com/... directly from the browser.

## Prerequisites & Setup

Before you can use this tool, you need to set up a Facebook App and obtain a User Access Token with the necessary permissions.

### 1. Create a Facebook App

1.  Go to [Facebook for Developers](https://developers.facebook.com/).
2.  Click on "**My Apps**" and then "**Create App**".
3.  Select an app type. For this purpose, "**Business**" is usually appropriate. Click "Next".
4.  Provide an "App Display Name" (e.g., "My Page Poster Tool") and your "App Contact Email".
5.  If prompted, select your Business Manager account (optional).
6.  Click "**Create App**" and complete any security checks.
7.  In any of the step you will have options. select **Manage everything on your Page**.

### 2. Configure App Use Cases / Products

1.  Once your app is created, you'll be taken to the App Dashboard.
2.  In the sidebar, find "**Use Cases**" and click "**Edit**" (or look for "Add Product" if "Use Cases" isn't prominent).
3.  Under "Build customized experiences for your Page", find the "**Manage everything on your Page**" use case and click "**Customize**".
4.  This will add the necessary APIs. You now need to configure permissions.

### 3. Add Permissions to Your App

1.  Search for the following permissions and request **Advanced Access** for each (you might be able to test in Development Mode with Standard Access initially, but for wider use or going live, Advanced Access and App Review are needed):
    *   `pages_manage_posts`: Allows your app to create, edit, and delete posts on Pages managed by a user.
    *   `pages_read_engagement`: Allows your app to read content posted by the Page, and read Page insights.
    *   `pages_show_list`: Allows your app to access the list of Pages a user manages.

3.  For development and testing, you might not need to submit for App Review immediately, but these permissions must be "added" to your app configuration.

### 4. Generate User Access Token

1.  In your App Dashboard, go to "**Tools**" > "**Graph API Explorer**".
2.  On the right side:
    *   **Facebook App**: Select the app you just created.
    *   **User or Page**: Select "**Get User Access Token**".
3.  A pop-up will appear. Under "**Permissions**", ensure you select AT LEAST the following:
    *   `pages_show_list`
    *   `pages_read_engagement`
    *   `pages_manage_posts`
    *   (If you plan to post videos) `publish_video`
4.  Click "**Generate Access Token**".
5.  You will be prompted to authorize the app with your Facebook account. Accept the permissions.
6.  The Graph API Explorer will now show a **User Access Token**. This is initially a short-lived token (expires in about 1-2 hours).

    **To get a Long-Lived User Access Token (recommended for extended use):**
    a. Copy the short-lived token.
    b. Go to the "**Access Token Debugger**" (Tools > Access Token Debugger or search for it).
    c. Paste your short-lived token and click "Debug".
    d. Click the "**Extend Access Token**" button at the bottom. This will generate a long-lived token (valid for about 60 days). Copy this new long-lived token.

## How to Use the Application

1.  Save the HTML code provided (the one with the UI enhancements) as an `.html` file (e.g., `fb_poster.html`).
2.  Open this `fb_poster.html` file in your web browser.
3.  **User Access Token**: Paste the User Access Token (preferably long-lived) you generated in the previous steps.
4.  **Message**: Type the text content for your post.
5.  **Page IDs**: Enter the Facebook Page IDs you want to post to, separated by commas (e.g., `123456789,987654321`). You can find a Page's ID by going to the Page's "About" section or using online tools.
6.  **Upload Images/Videos**: Click the file input area to select image(s) or a single video file.
7.  Click the "**Post to Facebook Pages**" button.
8.  The status of each post will appear in the "Post Status" section below the button.


