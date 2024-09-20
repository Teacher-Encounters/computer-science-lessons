# Node JS

You will learn the following

* Create a new Node.js project
* Run your code

There are endless tutorials online, so here I am only going to document the most basic version of the steps required to get started.

Open the terminal (in VS Code, or otherwise)

Run the following commands.

```
mkdir new-project
cd new-project
npm init -y
```

Open the folder of this project in your IDE and you should find it contains a `package.json` file.

Create a new file called `index.js` and give it the following contents.

```
// The usual
console.log('Hello World')
```

Open your `package.json` file and add a `start` script to the `scripts` object so that you can run your project with npm.

```json
{
    // ... other stuff
    "scripts": {
        "start": "node index.js",
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    // ... other stuff
}
```

Now in your command line run the following command.

```
npm start
```

You should see something like this.

![](<../.gitbook/assets/image (85) (1).png>)

We used the `prompt-sync` library in many of our early projects. In Repl.it we used their built in package manager. To replicate this process natively we must add a package to our project.

```
npm install prompt-sync
```

You can then import that library into your code and use it.

```javascript
const promptSync = require('prompt-sync');
const prompt = promptSync();

var name = prompt('What is your name? ');

console.log(`Hello ${name}`)
```

When I ran it, it looked like this.

![](<../.gitbook/assets/image (84) (1).png>)

You are now off and running.
