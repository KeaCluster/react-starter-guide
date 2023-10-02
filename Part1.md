# Part 1 - Setup, structure and basic info


In this part, we'll go through the steps to initialize a React project (No TSX) using Vite.js.

## Project Initialization with Vite.js

1. **Install Node.js**:
   - Ensure you have [Node.js](https://nodejs.org/en/) installed on your machine. Vite requires Node.js version 12.0.0 or higher. The latest stable release (LST) is always recommended. Remember that with Node.js npm should also be included.

2. **Create a new project**:
   - Open your terminal and run the following command to create a new project:
     ```bash
     npm create vite@latest my-react-app --template react
     ```
     Replace `my-react-app` with the desired project name. 

     - Make sure to select the proper options when running the command. If on windows, try executing the command on `cmd` or `git bash`. Sometimes either won't allow the use of arrow keys for selection.

     - First selection: **React**
     - Second: **Javascript**
     - If you select any other option, remember the solution can be to delete the project and start over.

3. **Navigate to your project directory**:
   - Once the project is created, navigate to the project directory:
     ```bash
     cd my-react-app
     ```

4. **Install dependencies**:
   - Install any necessary dependencies using npm. This command is only necessary for the initial setup and won't be required again unless running on a different device or dev environment. 
     ```bash
     npm install
     ```

5. **Start the development server**:
   - Now, start the development server:
     ```bash
     npm run dev
     ```
     This command will start the Vite development server, and you should be able to see your new React app running at [http://localhost:$PORT](http://localhost:$PORT) in your web browser. Change the `$PORT` space to adjust to the port `vite.js` just gave you. It's always on display on your console.

6. **Inspecting the project**:
   - You can now start inspecting your project! Open the `src` directory, and you'll find an `App.jsx` file where you can begin writing your React code. Remember to **study and inspect** before you make any changes.

## Directory Structure

Below is the directory structure for our React project initialized with Vite.js. If you are missing any directories make sure to create them.

```plaintext
/root
│
├── /public
│   ├── /images
│
├── /src
│   ├── /Components
│   ├── /assets
│   ├── App.css
│   ├── App.jsx
│   ├── index.css
│   └── main.jsx
│
├── README.md
├── index.html
├── package.json
└── vite.config.js

## Introduction to React

Basic information about React...

## JSX and Rendering

Explain JSX and rendering in React...
