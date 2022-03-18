# How to Develop a Reusable React Component on your Local Workstation (npm link) #


We wanted to provide flexibility for development workflow while creating React components.  There are at least 2 options:

*Local isolation* mode means you are developing the React component without the component being consumed by a local application (aggregator).  In other words, you want to develop a React component but aren't concerned with seeing it in the context of another application.

*Local integration* mode mean you want to see your component in context of a local application.

Prerequisites:
You have scaffolded a React component using the React component generator as described here:

Steps: **Local Isolation mode**
At the root of you scaffolded project type the following command:

npm run start
The build process will start and use Webpack development server to serve the project at: http://localhost:5000/.  When you make changes to code inside you project code files Hot Module Replacement refresh your browser automatically and you will see changes immediately.

Steps: Local Isolation mode
Example:  Let say you have a local application (Aggregator) that runs Webpack called Application A. In addition you have a local component project called *amazing-component*.

You will need to know your component name.  It is located in package.json file of the component project.
From the root directory of *amazing-component* type:

npm link

npm run build:watch

The command above (npm link) creates a symbolic link from your file system to the node_modules directory on your workstation
If you want to confirm the command above worked as expected type: *npm ls -g --depth=0*.  You should see *amazing-component* listed in the output.
Instead if you want to view any components linked locally in your project you can type from project root directory: 

*ls -l -R ./node_modules | grep ^l*

and see those components linked in your node_modules directory.
From the root directory of Application A type:

*npm link amazing-component*
The command above installs *amazing-component* in Application A.
Now you can type: npm run start in the root directory of Application A.


**Important note if you are developing a component using React Hooks:**

When linking *amazing-component* to Application A you may get an invalid-hook-call-warning when starting the aggregator application and it tries to render you component in the browser. This happens because both the component and the application are using their own instances of React and Hooks won't work if this is the case. So we need to tell *amazing-component* to point to Application A's instance of React. This is done the following way:

From *amazing-component* root directory: npm link Application A's root directory/node_modules/react
Kill the app and then npm run start.This should fix the problem. For further reference see the following:
https://reactjs.org/warnings/invalid-hook-call-warning.html
https://github.com/facebook/react/issues/15315


Once you are done with local integration mode do the following:
From the root directory of Application A type: **npm unlink *amazing-component***

The command above uninstalls *amazing-component* from local Application A.
From the root directory of *amazing-component* type:

**npm unlink**

The command above removes the  symbolic link from your file system and the local node_modules directory on your workstation.

At this point you should be ready to publish your component to NPM as a private package: 