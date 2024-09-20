# Unit Testing

For this task, you will take a 'fork' of the following repository.

{% embed url="https://github.com/Marling-School/node-typescript-starter" %}

I have done the basic project bootstrapping for Node, TypeScript and Jest.

Jest is a framework for unit testing code.

## Task 1 - Fork, Clone and Run

Take a fork of the GitHub project linked above. It will create an entire copy of the repository into your own user profile, which you can then treat as your own project.

Clone the GitHub repository on your laptop using the URL given by the GitHub page.

![](<../.gitbook/assets/image (86) (1).png>)

Run the `git clone`command to clone this repository to your local machine (replace the URL with the one from the page)

```bash
git clone <url from github>
```

Once you have cloned the project, do the following to install the dependencies and run the tests.

```
cd node-typescript-starter
npm install
npm test
```

This project includes a couple of simple maths functions and unit tests to check that they work.

Once you have successfully run the tests, you should receive some output like this.

![](<../.gitbook/assets/image (82) (1).png>)

> You will learn to love those green ticks

Attach the URL of your forked GitHub repo to the Google Classroom attachment.

## Task 2 - Add a new Maths Function with Test

The source code itself is in the `src` directory.

```
/src/simpleMaths.ts
/src/simplemaths.test.ts
```

As a convention, I used the filename with `.test` placed before the file extension to contain tests.

The existing functions calculate the area of simple shapes.

Add a function that does something mathsy (you can steal from your previous work if you like!) and then add unit tests in the `simpleMaths.test.ts` file.

Run the usual commands to commit and push your changes.

```
git add .
git commit -m 'adding a function to calculate highest common factor'
git push
```
