stage ('Build and SUT') {
    node {
        git 'https://github.com/cloudy-demos/aspnet-app'
        sh 'docker build -t aspnetapp .'
        sh 'docker run -it --rm -d --name aspnetapp -p 8000:80 aspnetapp'
    }
}

stage ('Check') {
    timeout(time: 10, unit: 'MINUTES') {
        input 'Does http://localhost:8000 look OK?'
    }
}

stage ('Destroy') {
    node {
        sh 'docker stop aspnetapp'
    }
}
