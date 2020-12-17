pipeline{
    agent any
    stages{
        stage('Etapa 1'){
            steps{
                echo 'Soy el primer paso de la etapa 1'
                git url: 'https://github.com/IvanciniGT/ejemploWebapp'
            }
        }
        stage('Etapa 2'){
            steps{
                echo 'Soy el primer paso de la etapa 2'
                sh 'mvn package'
            }
        }
        stage('Etapa 3'){
            steps{
                echo 'Despliegue'
                 deploy adapters: [tomcat9(credentialsId: '4f0f5d58-1e0c-4f09-bd6e-6354f6207a68', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miweb.war'
            }
        }
    }
    post{
        always{
            echo 'Yo me ejecuto siempre'
        }
        success{
            echo 'Yo me ejecuto cuando todo ha ido bien'
        }
        failure{
            echo 'Yo me ejecuto cuando ha ido mal'
        }
        changed{
            echo 'Yo me ejecuto si esta ejecución no acaba en el mismo estado que la anterior ejecucion'
        }
    }
}