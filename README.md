# How to Deploy a Routed React App to GitHub Pages

https://github.com/coding-to-music/deploy-react-app-to-gh-pages

From this article by Tomer Ben Rachel:

https://www.freecodecamp.org/news/deploy-a-react-app-to-github-pages/

In order for us to be able to upload our built application to GitHub Pages, we first need to install the gh-pages package.

```java
yarn add gh-pages
```

This package will help us to deploy our code to the gh-pages branch which will be used to host our application on GitHub Pages.

To allow us to use the gh-pages package properly, we need to add two keys to our scripts value in the package.json file:

```java
"scripts": {
    "start": "react-scripts start",
    "predeploy": "npm run build", <----------- #1
    "deploy": "gh-pages -d build", <---------- #2
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
```

Next, we need to modify our package.json file by adding the homepage field. This field is used by React to figure out the root URL in the built HTML file. In it, we will put the URL of our GitHub repository.

```java
{
  "name": "starter-project",
  "homepage": "https://tomerpacific.github.io/starter-project/", <----
  "version": "0.1.0",
  /....
}
```

To deploy our application, type the following in the terminal:

```java
npm run deploy
```

Running the command above takes care of building your application and pushing it to a branch called gh-pages, which GitHub uses to link with GitHub Pages.

🚧 If you did not name your remote origin, you will get an error during this phase stating that: Failed to get remote.origin.url (task must either be run in a git repository with a configured origin remote or must be configured with the "repo" option).
You will know that the process was successful if at the end of it you see the word Published. We can now head to our GitHub repository under Settings and scroll down to the GitHub Pages section.

If you see a message similar to the one above, it means your application is now hosted successfully on GitHub Pages.

My example:

https://github.com/coding-to-music/react-tracker

Has a directory called demo, and that is where the build files are located.

The top level package.json now has these new entries:

```java
  "scripts": {
    "buildDemo": "cd demo && npm run build",
    "deployDemo": "gh-pages -d demo/build",
  }
```

```java
npm run buildDemo
```

Output:

```java
> react-tracker@0.0.8 buildDemo
> cd demo && npm run build


> react-tracker-demo@0.1.0 build
> react-scripts build

Creating an optimized production build...
```

```java
npm run deployDemo
```

Output:

```java
> react-tracker@0.0.8 deployDemo
> gh-pages -d demo/build

Published
```

Check the progress of your deployment by visiting your GitHub repository under Settings and scroll down to the GitHub Pages section.

https://github.com/coding-to-music/react-tracker/settings/pages

Here is workflow for deploying to GitHub Pages:

https://github.com/coding-to-music/react-tracker/actions

The site is now live at https://coding-to-music.github.io/react-tracker/

This may also be helpful:

Open your package.json and add a homepage field:

```java
 "homepage": "http://myusername.github.io/my-app",
```

If you do this, Create React App will know to use /my-app as root URL.
