pipeline {
    agent any
    environment {
      PATH = "$PATH:/home/slave/flutter/bin"
      ANDROID_HOME="/home/slave/Android/Sdk"

    } 
    stages {
        stage('Build') {
            steps {
                sh "flutter doctor -v"
            }
        }
        stage('Build and Dockerize') {
            steps {
                dir('lib') {
                    // Étape de construction du projet Flutter
                
                     sh 'flutter pub get'
                     sh 'flutter build apk --release'

                    // Étape de construction de l'image Docker
                    // Assurez-vous que Docker est installé et accessible dans le chemin
                    bat "docker build -t flutter-img:${BUILD_ID} ."
                }
            }
        }
    }

    // Ajoutez d'autres directives du pipeline si nécessaire
    // ...
}
