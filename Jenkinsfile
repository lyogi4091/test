node {
    stage('Building Docker image'){
        checkout scm
        sh 'sudo docker build -t ubuntu_image_remotely .';
        sh 'sudo docker run -it -d --name testcontainer_remote_test -v /home/ciuser/test:/opt ubuntu_image_remotely';
        try {
            sh 'sudo docker exec testcontainer_remote_test pycodestyle--ignore=E501 python_good.py';
            echo 'python_good.py is in good format';
            }catch(x){
                println "python_good.py is in bad format";
                }
        try {
            sh 'sudo docker exec testcontainer_remote_ex2 pycodestyle--ignore=E501 python_bad.py';
            echo "python_bad.py is in good format";
            }catch(x){
                println "python_bad.py is in bad format";
                }
	}
}
