# VFloors360-Server
VFloors360-Server is a Node.js-based backend application that powers the VFloors360 virtual environment. It provides RESTful APIs for managing tile data, user interactions, and room navigation. The server is responsible for handling user authentication, storing data with MongoDB, and ensuring secure and efficient processing of requests to support smooth and responsive system performance.

> **Project Name:** VFloors360-Server  
> **Repository:** [GitHub - khalid-syfullah/VFloors360-Server](https://github.com/khalid-syfullah/VFloors360-Server)


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#description">Description</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#project-structure">Project Structure</a></li>
    <li><a href="#installation">Installation</a></li>
    <li><a href="#api-endpoints">API Endpoints</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
  </ol>
</details>

## Description

<p align="center">
    VFloors360 API is a backend system designed to manage and facilitate the operations of a virtual reality environment, providing endpoints for room navigation, tile management, user authentication, and more.
    <br />
    
</p>

## Features
- User Authentication and Authorization.
- Interactive 360° Room Navigation.
- Tile Selection and Favoriting.
- Room and Tile Management.
- Comprehensive Logging and Error Handling.

## Built With

* [Node.js](https://nodejs.org/): Backend environment for running the API server.
* [Express.js](https://expressjs.com/): Web framework for Node.js used in handling API requests.
* [MongoDB](https://www.mongodb.com/): NoSQL database used for storing data.
* [Mongoose](https://mongoosejs.com/): Object Data Modeling (ODM) library for MongoDB and Node.js.
* [JWT](https://jwt.io/): For secure user authentication.
* [Mocha](https://mochajs.org/): Test framework for Node.js.
* [Chai](https://www.chaijs.com/): Assertion library for testing.

## Project Structure

<div class="folder-structure">
    <p>📦 VFloors360-Server<br>
    ┣ 📂 controllers<br>
    ┃ ┣ 📜 adminController.js<br>
    ┃ ┣ 📜 authController.js<br>
    ┃ ┣ 📜 errorController.js<br>
    ┃ ┣ 📜 roomController.js<br>
    ┃ ┣ 📜 softwareDataController.js<br>
    ┃ ┣ 📜 tileController.js<br>
    ┃ ┗ 📜 voiceoverController.js<br>
    ┣ 📂 middleware<br>
    ┃ ┣ 📜 authMiddleware.js<br>
    ┃ ┣ 📜 errorMiddleware.js<br>
    ┃ ┗ 📜 validatorMiddleware.js<br>
    ┣ 📂 models<br>
    ┃ ┣ 📜 Room.js<br>
    ┃ ┣ 📜 Tile.js<br>
    ┃ ┣ 📜 User.js<br>
    ┃ ┗ 📜 Voiceover.js<br>
    ┣ 📂 routes<br>
    ┃ ┣ 📜 adminRoutes.js<br>
    ┃ ┣ 📜 authRoutes.js<br>
    ┃ ┣ 📜 roomRoutes.js<br>
    ┃ ┣ 📜 softwareRoutes.js<br>
    ┃ ┣ 📜 tileRoutes.js<br>
    ┃ ┣ 📜 voiceoverRoutes.js<br>
    ┃ ┗ 📜 vrRoutes.js<br>
    ┣ 📂 test<br>
    ┃ ┣ 📜 auth.test.js<br>
    ┃ ┣ 📜 middleware.test.js<br>
    ┃ ┗ 📜 room.test.js<br>
    ┣ 📂 utils<br>
    ┃ ┣ 📜 generateToken.js<br>
    ┃ ┗ 📜 logger.js<br>
    ┣ 📜 .gitignore<br>
    ┣ 📜 jest.config.js<br>
    ┣ 📜 server.js<br>
    ┗ 📜 README.md</p>
</div>

## Installation

1. Clone the repo
   ```sh
   git clone https://github.com/Khalid-Syfullah/VFloors360-Server.git

2. Install dependencies
   
   ```sh
   npm install

3. Run TPT VR System API project for production
   ```sh
   npm start

4. Run TPT VR System API project in development
   
   ```sh
   npm run dev

5. Run unit test
   
   ```sh
   npm test


## API Endpoints

### Retrieve Tasks

- **GET `/tasks`**
  - **Description:** Retrieves a list of all tasks.
  - **Parameters:** None
  - **Returns:** An array of task objects.

- **GET `/tasks/:id`**
  - **Description:** Retrieves a specific task by its unique ID.
  - **Parameters:**
    - `id` (string): The ID of the task to retrieve.
  - **Returns:** The task object corresponding to the provided ID.


## API Endpoints

### Admin Routes

- **POST /create-admin**
  - **Description: Creates a new admin.**
  - **Request Body: JSON object with admin details (e.g., username, password, role).**
  - **Returns: The created admin object.**
    
- **POST /login`**
  - **Description: Logs in an admin and returns a token.**
  - **Request Body: JSON object with login credentials (e.g., username, password).**
  - **Returns: A token for authenticated admin access.**
  
- **POST /logout**
  - **Description: Logs out the admin.**
  - **Middleware: authMiddleware (ensures the user is authenticated).**
  - **Returns: Success message indicating successful logout.**

### Auth Routes

- **POST /login**
  - **Description: Logs in a user and returns a token.**
  - **Request Body: JSON object with login credentials (e.g., username, password).**
  - **Returns: A token for authenticated user access.**

- **POST /register**
  - **Description: Registers a new user.**
  - **Request Body: JSON object with user details (e.g., username, password).**
  - **Returns: The registered user object.**

- **POST /logout**
  - **Description: Logs out the user.**
  - **Middleware: authMiddleware (ensures the user is authenticated).**
  - **Returns: Success message indicating successful logout.**

### Room Routes

- **GET /rooms**
  - **Description: Retrieves a list of all rooms.**
  - **Parameters:** None
  - **Returns: An array of room objects.**

- **GET /rooms/:id**
  - **Description: Retrieves a specific room by its unique ID.**
  - **Parameters:**
    - id (string): The ID of the room to retrieve.
  - **Returns: The room object corresponding to the provided ID.**

- **POST /rooms**
  - **Description: Creates a new room.**
  - **Middleware: authMiddleware (only authenticated admins can add rooms).**
  - **Request Body: JSON object containing room details (e.g., name, description, image).**
  - **Returns: The created room object with assigned ID.**

- **PUT /rooms/:id**
  - **Description: Updates an existing room identified by its ID.**
  - **Parameters:**
    - id (string): The ID of the room to update.
  - **Middleware: authMiddleware (only authenticated admins can update rooms).**
  - **Request Body: JSON object containing updated room details, including optional tile information.**
  - **Returns: The updated room object.**

- **DELETE /rooms/:id**
  - **Description: Deletes a room specified by its ID.**
  - **Parameters:**
    - id (string): The ID of the room to delete.
  - **Middleware: authMiddleware (only authenticated admins can delete rooms).**
  - **Returns: Success message indicating the room deletion.**

- **POST /rooms/:id/navigate**
  - **Description: Navigates a room.**
  - **Parameters:**
    - id (string): The ID of the room to navigate.
  - **Middleware: authMiddleware (only authenticated admins can navigate rooms).**
  - **Returns: Success message indicating navigation action.**

- **POST /rooms/:id/upload-model**
  - **Description: Uploads a room model file.**
  - **Parameters:**
    - id (string): The ID of the room to upload the model for.
  - **Middleware: authMiddleware (only authenticated admins can upload models).**
  - **Request Body: Model file.**
  - **Returns: Success message indicating the model upload.**

- **GET /rooms/:id/download-model**
  - **Description: Downloads a room model file.**
  - **Parameters:**
    - id (string): The ID of the room to download the model for.
  - **Middleware: authMiddleware (only authenticated admins can download models).**
  - **Returns: The model file.**

- **DELETE /rooms/:id/delete-model**
  - **Description: Deletes a room model file.**
  - **Parameters:**
    - id (string): The ID of the room to delete the model from.
  - **Middleware: authMiddleware (only authenticated admins can delete models).**
  - **Returns: Success message indicating the model deletion.**

### Tile Routes
- **GET /tiles**
  - **Description: Retrieves a list of all tiles.**
  - **Parameters:** None
  - **Returns: An array of tile objects.**

- **GET /tiles/:id**
  - **Description: Retrieves a specific tile by its unique ID.**
  - **Parameters:**
    - id (string): The ID of the tile to retrieve.
  - **Returns: The tile object corresponding to the provided ID.**

- **POST /tiles**
  - **Description: Creates a new tile.**
  - **Middleware: authMiddleware (only authenticated admins can add tiles).**
  - **Request Body: JSON object containing tile details.**
  - **Returns: The created tile object with assigned ID.**

- **PUT /tiles/:id**
  - **Description: Updates an existing tile identified by its ID.**
  - **Parameters:**
    - id (string): The ID of the tile to update.
  - **Middleware: authMiddleware (only authenticated admins can update tiles).**
  - **Request Body: JSON object containing updated tile details.**
  - **Returns: The updated tile object.**

- **DELETE /tiles/:id**
  - **Description: Deletes a tile specified by its ID.**
  - **Parameters:**
    - id (string): The ID of the tile to delete.
  - **Middleware: authMiddleware (only authenticated admins can delete tiles).**
  - **Returns: Success message indicating the tile deletion.**

- **POST /tiles/:id/select**
  - **Description: Selects a tile.**
  - **Parameters:**
    - id (string): The ID of the tile to select.
  - **Middleware: authMiddleware (only authenticated admins can select tiles).**
  - **Returns: Success message indicating the tile selection.**

- **POST /tiles/:id/favorite**
  - **Description: Favorites a tile.**
  - **Parameters:**
    - id (string): The ID of the tile to favorite.
  - **Middleware: authMiddleware (only authenticated admins can favorite tiles).**
  - **Returns: Success message indicating the tile favoriting.**

- **POST /tiles/:id/upload-model**
  - **Description: Uploads a tile model file.**
  - **Parameters:**
    - id (string): The ID of the tile to upload the model for.
  - **Middleware: authMiddleware (only authenticated admins can upload models).**
  - **Request Body: Model file.**
  - **Returns: Success message indicating the model upload.**

- **GET /tiles/:id/download-model**
  - **Description: Downloads a tile model file.**
  - **Parameters:**
    - id (string): The ID of the tile to download the model for.
  - **Middleware: authMiddleware (only authenticated admins can download models).**
  - **Returns: The model file.**

- **DELETE /tiles/:id/delete-model**
  - **Description: Deletes a tile model file.**
  - **Parameters:**
    - id (string): The ID of the tile to delete the model from.
  - **Middleware: authMiddleware (only authenticated admins can delete models).**
  - **Returns: Success message indicating the model deletion.**

### Software Routes

- **GET /software**
  - **Description: Retrieves software data.**
  - **Parameters:** None
  - **Returns: Software data.**

### Voiceover Routes
- **GET /voiceovers**
  - **Description: Retrieves voiceover data.**
  - **Parameters:** None
  - **Returns: Voiceover data.**

### VR Routes
- **GET /vr**
  - **Description: Retrieves VR data.**
  - **Parameters:** None
  - **Returns: VR data.**

### Test Routes
- **GET /**
  - **Description: Returns the API version and a welcome message.**
  - **Parameters:** None
  - **Returns: JSON object with status, message, and timestamp.**

- **GET /some-protected-route**
  - **Description: A protected route to test authentication.**
  - **Middleware: authMiddleware (ensures the user is authenticated).**
  - **Returns: Success message indicating access to the protected route.**

Each endpoint is designed to facilitate CRUD operations (Create, Read, Update, Delete) on tasks via backend API. The placeholders have to be replaced with API URL with actual implementation details where applicable.



<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/Khalid-Syfullah/VFloors360-Server/issues) for a list of proposed features (and known issues).



<!-- CONTRIBUTING -->
## Contributing

Follow these steps to fork and create a pull request:

### 🛠 Steps to Contribute

1. **Fork** the repository by clicking the "Fork" button on the top right of the [main repo page](https://github.com/Khalid-Syfullah/VFloors360-Server).
2. **Clone** your forked repository to your local machine:
   ```bash
   git clone https://github.com/Khalid-Syfullah/VFloors360-Server.git
   cd VFloors360-Admin
   ```
3. **Create a new branch** from `main`:
   ```bash
   git checkout -b your-username/feature-name
   ```
4. **Make your changes** and commit them:
   ```bash
   git add .
   git commit -m "Describe your changes"
   ```
5. **Push your branch** to your fork:
   ```bash
   git push origin your-username/feature-name
   ```
6. **Open a Pull Request** on GitHub:
   - Go to your forked repository.
   - Click "Compare & pull request".
   - Ensure the base repository is `Khalid-Syfullah/VFloors360-Server` and the base branch is `main`.
   - Add a clear title and description of your changes.
   - Submit the PR!



### 📌 Guidelines

- Keep your commits atomic and descriptive.
- Follow existing coding conventions.
- If you're unsure, open an issue first to discuss the change.



## 📜 License

MIT © [khalid-syfullah](https://github.com/khalid-syfullah)
