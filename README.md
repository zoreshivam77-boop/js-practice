# Node.js Express App 

A small Node.js application built with Express. It serves a text message at the root URL and is demonstrated running on an AWS EC2 instance on port `3000`.

## Project details

- **Project name:** `Deployment of Node.js apllication`
- **Port:** `3000`
- **Start command:** `npm start`

## Project files

- `app.js` — creates the Express app, defines the `/` route, and starts the HTTP server.
- `package.json` — project metadata, start script, and dependency declaration.
- `package-lock.json` — npm's dependency lockfile
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

## Deploy on AWS EC2

These are the high-level steps used for the demonstrated deployment.

1. Launch an EC2 instance and install Node.js/npm.
2. Clone the project repository onto the instance.

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
