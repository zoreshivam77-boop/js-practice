# Node.js Express App — Jenkins Webhook Deployment

A small Node.js application built with Express. It serves a text message at the root URL and is demonstrated running on an AWS EC2 instance on port `3000`.

## Project details

- **Project name:** `jenkins-node-app`
- **Entry point:** `app.js`
- **Framework:** Express.js
- **Port:** `3000`
- **Start command:** `npm start`

## Project files

- `app.js` — creates the Express app, defines the `/` route, and starts the HTTP server.
- `package.json` — project metadata, start script, and dependency declaration.
- `package-lock.json` — npm's dependency lockfile, if included in the repository.
- `README.md` — project documentation.
- `Screenshot 2026-10-10 104902.png` — screenshot of the deployed app in a browser.

## Application behavior

The application defines a `GET /` route. When someone visits the root URL, Express responds with:

> Hiii from jenkins, added webhook, we are from 18 May Devops batch

When the server starts, the application logs a message indicating that it is listening on port `3000`.

## Requirements

- Node.js and npm
- Internet access to install dependencies
- An environment that can accept HTTP traffic on port `3000` for the browser test

## Run locally

1. Install Node.js and npm.
2. Open a terminal in the folder containing `package.json`.
3. Install the dependencies:

   ```bash
   npm install
   ```

4. Start the app:

   ```bash
   npm start
   ```

5. Open `http://localhost:3000` in your browser.

You can also start it with `node app.js`.

## Deploy on AWS EC2

These are the high-level steps used for the demonstrated deployment. Exact commands can vary by operating system and setup.

1. Launch an EC2 instance and install Node.js/npm.
2. Clone the project repository onto the instance.
3. Change into the project directory (the directory containing `package.json`):

   ```bash
   cd js-practice
   ```

   Use your actual cloned directory name if it differs.

4. Install dependencies:

   ```bash
   npm install
   ```

5. Start the app:

   ```bash
   npm start
   ```

6. In the EC2 security group's inbound rules, allow TCP port `3000` from your IP for testing. Avoid exposing development ports broadly unless needed.
7. Visit:

   `http://YOUR-EC2-PUBLIC-IP:3000`

The attached screenshot shows the application responding at a public EC2 IP on port `3000` and displaying the expected message.

## Jenkins/webhook context

The response text mentions Jenkins and a webhook. The supplied `app.js` only defines an Express route and starts the Node.js server; it does **not** itself configure a Jenkins job or webhook. Jenkins/webhook automation would need to be configured separately.

## Troubleshooting

### `Cannot find module 'express'`

Run `npm install` from the project directory where `package.json` is located. Running it from `/root` or another directory without the project's `package.json` will not install this project's dependencies.

### `ENOENT: no such file or directory, open '.../package.json'`

Change to the correct project directory and confirm the file exists:

```bash
pwd
ls -la
```

### Browser cannot reach the app

- Confirm `node app.js` or `npm start` is still running.
- Confirm the app listens on port `3000`.
- Confirm the EC2 security group permits inbound TCP port `3000`.
- Check the instance's current public IPv4 address.

## Screenshot: successful output

Save the supplied screenshot alongside this README using the filename:

`Screenshot 2026-10-10 104902.png`

It shows the browser displaying the app's response at `3.85.216.116:3000`.

![Node.js Express app running on EC2](Screenshot%202026-10-10%20104902.png)

## Learning outcomes

This project demonstrates:

- Creating a basic Express server.
- Defining a GET route.
- Installing Node.js dependencies with npm.
- Starting an application with an npm script.
- Hosting a small web app on EC2.
- Testing access through a public IP and port.
- Troubleshooting missing dependencies and incorrect working directories.
