```groovy
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Compilando / preparando entorno...'
                bat 'python --version'
                bat 'pipenv --version'
            }
        }

        stage('Test') {
            steps {
                script {
                    int resultado = bat(
                        script: 'pipenv run pytest',
                        returnStatus: true
                    )

                    if (resultado == 0) {
                        echo 'Pruebas ejecutadas correctamente.'
                    } else {
                        error "Las pruebas fallaron o no pudieron ejecutarse. Código de salida: ${resultado}"
                    }
                }
            }
        }

        stage('Analyze') {
            steps {
                echo 'Etapa de análisis de calidad de código.'
                echo 'La integración real con SonarQube debe configurarse por separado.'
            }
        }

        stage('Dependency Management') {
            steps {
                bat 'pipenv install'
                bat 'pipenv graph'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Despliegue simulado en entorno de prueba.'
            }
        }

    }
}
```