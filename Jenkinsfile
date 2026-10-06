pipeline {
    agent any
    tools {
        nodejs "Nodejs"
    }
    stages {
        stage ( "Checkout") {
            steps {
                checkout scm
            }
        }
        stage('Install Packages') {
    steps {
        bat 'python -m pip install -r requirements.txt'
    }
}
        stage ("test") {
            steps {
                    bat "npx ng text --no-watch --no-progress --browser=Chromeheadless"
                 echo "testing"
                 }
        }
        stage ("build") {
            steps {
                    bat "npx ng build --configuration production"
                }
        }
        stage ("Deployment")  {
               steps  {
                 bat  "del /q /s c:\\inetpub\\wwwroot\\PythonApp\\*"
                 bat  "xcopy /E /Y /I dist\\PythonApp\\browser\\* c:\\inetpub\\wwwroot\\PythonApp\\"
                      }       
            }
    }
    post {
       success {
            echo "Angular application build successfully"
       }
        failure {
            echo "Build Failed"
        }
    }
}
