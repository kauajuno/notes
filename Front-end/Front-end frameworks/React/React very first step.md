To really start messing around with react, it's necessary to set up an environment to do so, and in order to do this it's necessary to install [[Node.js|node.js]], which will come with [[npm]]. Once you've done it, you got all you need to create your very first react app.

# Using create-react-app

The more classic way of creating a react app.

```
npx create-react-app first-app
```

By running the command above, you'll be setting up a react project inside a new folder called first-app. You can actually switch the name to whichever name you want, or to `.` if you're already in the folder you want to setup the project in as you run this command.

# Using Vite

The more modern approach.

```
npm init vite
```

By running the command above, you'll be setting up a react project inside a new folder which name will be asked to you through Vite's CLI, as well as other configurations such as which framework you want to use (in this case, React) and other basic configurations (in this case, it will ask if you want to use React with JavaScript or TypeScript, choose JavaScript if you're a beginner).

Make sure to follow the instructions given by Vite in the terminal, as running `npm i` after getting to the project folder is essential to install the dependencies.

>[!info]
>Vite offers an advantage over create-react-app by having features such as HMR and smaller bundles.