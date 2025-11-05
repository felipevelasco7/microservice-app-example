# Frontend

UI for sample distributed TODO application.

## Configuration
- `PORT` - a port the application binds to 
- `AUTH_API_ADDRESS` - address of `auth-api` for authentication
- `TODOS_API_ADDRESS` - address of `todos-api` for TODO CRUD

## Building

``` bash
# install dependencies
npm install --legacy-peer-deps

# build application
npm run build
```

## Running

``` bash
PORT=8080 AUTH_API_ADDRESS=http://127.0.0.1:8000 TODOS_API_ADDRESS=http://127.0.0.1:8082 npm start
```

## Updated Build and Deployment Instructions

### Step-by-Step Commands

1. **Install Dependencies**
   ```bash
   npm install --legacy-peer-deps
   ```
   Use the `--legacy-peer-deps` flag to bypass peer dependency conflicts.

2. **Build the Application**
   ```bash
   npm run build
   ```
   This compiles the Vue.js frontend into static assets.

3. **Build the Docker Image**
   ```bash
   docker build -t felipevelasco7/frontend:latest ./frontend
   ```
   This creates a Docker image with a multi-stage build (Node.js for building, nginx for serving).

4. **Run the Docker Container**
   ```bash
   docker run -p 8080:80 felipevelasco7/frontend:latest
   ```
   This serves the frontend on `http://localhost:8080`.

### Dependencies Updated

| Dependency                | Version   |
|---------------------------|-----------|
| Node                      | 16.x      |
| NPM                       | 8.x       |
| webpack                   | ^3.12.0   |
| vue-loader                | ^12.1.0   |
| css-loader                | ^0.28.5   |
| sass-loader               | ^6.0.7    |
| extract-text-webpack-plugin | ^3.0.2 |

### Resolved Issues

1. **Peer Dependency Conflicts**
   - Used `--legacy-peer-deps` to resolve npm installation issues caused by strict peer dependency checks.

2. **Webpack Configuration**
   - Downgraded to webpack 3 to match legacy project requirements.
   - Replaced `mini-css-extract-plugin` with `extract-text-webpack-plugin`.
   - Updated `vue-loader` and other loaders to compatible versions.

3. **Docker Build**
   - Switched to Node.js 16 for compatibility with the project's build script.
   - Used a multi-stage Dockerfile to build and serve the application efficiently.

## Dependencies
Here you can find the software required to run this microservice, as well as the version we have tested. 
|  Dependency | Version  |
|-------------|----------|
| Node        | 8.17.0   |
| NPM         | 6.13.4   |