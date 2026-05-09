node {
    def DOCKERHUB_USERNAME = 'sonamlindel19'
    def STUDENT_ID = '02250369'
    def BACKEND_IMAGE = "${DOCKERHUB_USERNAME}/be-todo:${STUDENT_ID}"
    def FRONTEND_IMAGE = "${DOCKERHUB_USERNAME}/fe-todo:${STUDENT_ID}"

    stage('Checkout Code') {
        checkout scm
    }

    stage('Check Node and NPM') {
        bat 'node -v'
        bat 'npm -v'
    }

    stage('Install Backend Dependencies') {
        dir('SonamLindel_02250369_DSO101_A1_and_A2/backend') {
            bat 'npm install'
        }
    }

    stage('Install Frontend Dependencies') {
        dir('SonamLindel_02250369_DSO101_A1_and_A2/frontend') {
            bat 'npm install'
        }
    }

    stage('Build Frontend') {
        dir('SonamLindel_02250369_DSO101_A1_and_A2/frontend') {
            bat 'npm run build'
        }
    }

    stage('Run Backend Tests') {
        dir('SonamLindel_02250369_DSO101_A1_and_A2/backend') {
            bat 'npm test'
        }
    }

    stage('Build Docker Images') {
        bat "docker build -t ${BACKEND_IMAGE} ./SonamLindel_02250369_DSO101_A1_and_A2/backend"
        bat "docker build -t ${FRONTEND_IMAGE} ./SonamLindel_02250369_DSO101_A1_and_A2/frontend"
    }

    stage('Push Docker Images') {
        withCredentials([usernamePassword(
            credentialsId: 'docker-hub-creds',
            usernameVariable: 'DOCKER_USER',
            passwordVariable: 'DOCKER_PASS'
        )]) {
            bat 'echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
            bat "docker push ${BACKEND_IMAGE}"
            bat "docker push ${FRONTEND_IMAGE}"
        }
    }
}