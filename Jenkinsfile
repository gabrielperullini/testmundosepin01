pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Clonar el repositorio de código desde Git
                checkout scm
            }
        }
        
        stage('Build and Test') {
            steps {
                // Construir la aplicación y ejecutar pruebas de integración (usando Mocha)
                sh 'npm install'
                sh 'npm test'
            }
        }
        
        stage('Security Analysis') {
            steps {
                // Ejecutar análisis de seguridad utilizando Trivy en la imagen de Docker
                sh 'docker build -t myapp .'
                sh 'trivy myapp'
            }
        }
        
        stage('Deploy') {
            steps {
                // Construir y desplegar la imagen de Docker
                sh 'docker build -t myapp .'
                sh 'docker run -p 8080:8080 myapp'
            }
        }
    }
}
