pipeline {
    agent any

    stages {
        stage('Instalar dependencias') {
            steps {
                bat '''
                    python -m venv venv
                    call venv\\Scripts\\activate
                    pip install -r requirements.txt || echo No hay archivo requirements.txt
                '''
            }
        }

        stage('Ejecutar pruebas') {
            steps {
                bat '''
                    call venv\\Scripts\\activate
                    python test_main.py
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente.'
        }
        failure {
            echo 'Ocurrió un error en la ejecución del pipeline.'
        }
    }
}
