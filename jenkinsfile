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
            checkout scm
        }
        
        // Stage 2: Build the project (this can be adjusted for your tech stack)
        stage('Build') {
            echo 'Building the project...'
            // For example, if you use Maven for a Java project
            // sh 'mvn clean install'
            
            // If it's a Node.js project
            sh 'npm install'
        }

        // Stage 3: Run tests
        stage('Test') {
            echo 'Running tests...'
            // Example for running tests (adjust based on your tech stack)
            // sh 'mvn test'  // For Java projects
            // sh 'npm test'  // For Node.js projects
        }
        
        // Stage 4: Deploy to staging environment
        stage('Deploy to Staging') {
            echo 'Deploying to staging environment...'
            // You can use `sh` or `bat` to execute deploy commands
            // Example: 
            // sh 'kubectl apply -f deployment.yaml'
            // Or deploy to your cloud provider or test server
            echo 'Deploying application...'
        }

        // Optional: Archive build artifacts or deploy to production
        stage('Archive') {
            echo 'Archiving build artifacts...'
            archiveArtifacts '**/target/*.jar'  // Adjust for your build artifacts (e.g., JAR files for Java)
        }

    } catch (Exception e) {
        currentBuild.result = 'FAILURE'
        throw e
    } finally {
        // Clean up workspace or perform post-build actions
        cleanWs()
    }
}
