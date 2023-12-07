@Library('my-shared-librabry') _
pipeline{
    agent any

    stages{
        
        stage('Git Checkout'){
        steps {
            gitCheckout(
                branch: "main",
                url: 'https://github.com/suyogIsdevopsEngineer/Java_app.git'
            )
                
            }
        }

    }
    }

    
}