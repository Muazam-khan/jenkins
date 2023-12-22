// Demo on scripted pipeline
node {
    stage('Test'){
        print 'Hello World'
    }
    if(env.TAG_NAME == ""){
    stage('Runs on Tag Name'){
        print 'I love tags'
    }
    }
    else {
        stage('Runs on Branch Name'){
        print 'Runs on branch'

    }
}
}