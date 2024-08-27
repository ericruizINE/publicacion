pipeline {
  agent any
  stages {
    stage('Versión Python') {
      steps {
        sh 'python3 --version'
      }
    }
    stage('Descarga de CSV y extracción de archivos') {
      steps {
        sh 'python3 24-05-07-BD-Descarga-Descomprimir_1.py'
      }
    }
    stage('Ejecución de WebDriver y validación de datos sitio publicación VS Archivo CSV Presidencia') {
      steps {
        sh 'python3 publicacion.py'
      }
    }
    stage('Reports') {
            steps {
                script {
                        allure([
                                includeProperties: false,
                                jdk: '',
                                properties: [],
                                reportBuildPolicy: 'ALWAYS',
                                results: [[path: 'target/allure-results']]
                        ])
                }
            }
  }
}
