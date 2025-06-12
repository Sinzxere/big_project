# Money Saver Application

A full-stack application for tracking income and expenses, built with Go, React, and PostgreSQL.

## Project Structure

```
.
├── backend/           # Go backend service
├── frontend/         # React frontend application
└── k8s/             # Kubernetes manifests with Kustomize
    ├── base/        # Base configuration
    └── overlays/    # Environment-specific configurations
        ├── dev/     # Development environment
        └── prod/    # Production environment
```

## Prerequisites

- Go 1.21 or later
- Node.js 18 or later
- Docker
- Kubernetes cluster
- PostgreSQL

## Setup

### Backend

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   go mod download
   ```

3. Build the Docker image:
   ```bash
   docker build -t money-saver-backend:latest .
   ```

### Frontend

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build the Docker image:
   ```bash
   docker build -t money-saver-frontend:latest .
   ```

## Database Setup

1. Create a PostgreSQL database:
   ```sql
   CREATE DATABASE money_saver;
   ```

2. Create a Kubernetes secret for database credentials:
   ```bash
   kubectl create secret generic db-secret \
     --from-literal=username=postgres \
     --from-literal=password=your_password
   ```

## Deployment

### Development Environment

1. Apply the development configuration:
   ```bash
   kubectl apply -k k8s/overlays/dev
   ```

### Production Environment

1. Apply the production configuration:
   ```bash
   kubectl apply -k k8s/overlays/prod
   ```

## Accessing the Application

- Frontend: http://localhost:80
- Backend API: http://localhost:8080

## API Endpoints

- GET /api/transactions - Get all transactions
- POST /api/transactions - Create a new transaction
- DELETE /api/transactions/{id} - Delete a transaction

## Development

### Backend

1. Run the backend service locally:
   ```bash
   cd backend
   go run main.go
   ```

### Frontend

1. Run the frontend development server:
   ```bash
   cd frontend
   npm start
   ```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request 