node('built-in')
{
    stage('checkout_master') {
        git  "https://github.com/flappa83/Netrox-WebApp.git"
    }

    stage('continuous build_master'){
    sh label: '', script: 'mvn package'
    }

}
