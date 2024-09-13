pipeline {
    agent any

    triggers {
        // Trigger the pipeline when a Pull Request is created or updated
        githubPullRequest()
    }

    environment {
        GIT_REPO_URL = 'https://github.com/hemalatha-Alla/SampleJenkins.git' // Replace with your GitHub repo URL
        BRANCH_NAME = 'release/test' // Replace with the branch name to build from
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository from GitHub...'
                // Clone the GitHub repository using the specified branch
                git branch: "release/test", url: "https://github.com/hemalatha-Alla/SampleJenkins"
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Run Maven clean install to build the project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Run Maven tests
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build and tests were successful.'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
