# Assignment #5 - Dockerize a Recipe Sharing Application

A full-stack recipe sharing application with React frontend and Node.js backend.

## Your Assignment
Your task is to containerize this application using Docker and Docker Compose. You'll need to create:
1. `frontend/Dockerfile` - To containerize the React app
2. `backend/Dockerfile` - To containerize the Node.js API
3. `docker-compose.yml` - To orchestrate both services

Once completed, users should be able to run the entire application with a single command: `docker-compose up`.

Good luck! 🚀

## Local Development Setup

### Prerequisites
- Node.js 16 or higher
- npm

### Running the Application Locally

1. **Start the Backend:**
```bash
cd backend
npm install
npm start
```
Backend will run on `http://localhost:8080`. You can preview all recipes at `http://localhost:8080/api/recipes`.

2. **Start the Frontend (in a new terminal)**:
```bash
cd frontend
npm install
npm run dev
```
Frontend will run on `http://localhost:3000` (or the next available port).

3. **Test the Application**:
    - Visit the URL shown in your terminal (Usually `http://localhost:3000`)
    - You should see sample recipes loaded
    - Try adding a new recipe using the form
    - Refresh the page to verify data persistence
    - You can also see that it has been added in the backed by visiting or refreshing `http://localhost:8080/api/recipes`

## API Endpoints
- `GET /api/recipes` - Get all recipes
- `GET /api/recipes/:id` - Get single recipe
- `POST /api/recipes` - Create new recipe
- `DELETE /api/recipes/:id` - Delete recipe
- `GET /api/health` - Health check

## CI/CD Pipeline

GitHub Actions runs the backend and frontend test suites for every push and pull request to `main`.
Deployment is a separate job that depends on the test job, so failed tests prevent deployment.
Successful pushes to `main` build both Docker images, store them in Google Artifact Registry,
and deploy the backend and frontend to Google Cloud Run.

The workflow requires these GitHub Actions repository secrets:

- `GCP_PROJECT_ID`
- `GCP_REGION`
- `GCP_SA_KEY`

The Google Cloud project also needs an Artifact Registry Docker repository named `recipe-app`.

## Project Structure
```bash
recipe-app/
├── frontend/       # React application (Vite)
├── backend/        # Node.js/Express API
└── README.md       # This file
```
