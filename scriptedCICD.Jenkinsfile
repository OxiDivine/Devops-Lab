node {
    // Define workspace or use default workspace
    def workspace = pwd()
    
    // Define environment variables if needed
    environment {
        GIT_REPO = 'https://github.com/OxiDivine/Devops-Lab.git'
        BRANCH = 'main'
    }

    try {
        // Stage 1: Checkout the code from the Git repository
        stage('Checkout') {
            echo 'Checking out code from Git repository...'
            checkout([
                $class: 'GitSCM',
                branches: [[name: "*/${BRANCH}"]],
                userRemoteConfigs: [[url: "${GIT_REPO}"]]
            ])
        }
        
        // Stage 2: Build the project (Windows compatible)
        stage('Build') {
            echo 'Building the project...'
            
            // For Maven Java project on Windows:
            bat 'mvn clean install'
            
            // For Node.js project on Windows:
            // bat 'npm install'
            
            // For .NET project:
            // bat 'dotnet build'
        }

        // Stage 3: Run tests (Windows compatible)
        stage('Test') {
            echo 'Running tests...'
            
            // For Maven tests:
            bat 'mvn test'
            
            // For Node.js tests:
            // bat 'npm test'
            
            // For .NET tests:
            // bat 'dotnet test'
        }
        
        // Stage 4: Deploy to staging environment
        stage('Deploy to Staging') {
            echo 'Deploying to staging environment...'
            
            // Example deployment commands for Windows:
            // bat 'kubectl apply -f deployment.yaml'
            // Or for Azure:
            // bat 'az webapp deployment source config-zip --resource-group myResourceGroup --name myAppName --src target/myapp.zip'
            
            echo 'Deployment commands would execute here...'
        }

        // Optional: Archive build artifacts
        stage('Archive') {
            echo 'Archiving build artifacts...'
            
            // Archive JAR files for Java projects:
            archiveArtifacts 'target/*.jar'
            
            // Or for Node.js projects:
            // archiveArtifacts 'build/**/*'
        }

    } catch (Exception e) {
        currentBuild.result = 'FAILURE'
        error "Pipeline failed: ${e.getMessage()}"
    } finally {
        // Clean up workspace
        cleanWs()
    }
}
