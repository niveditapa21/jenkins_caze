pipeline {
    agent any
    stages {
        stage('Test Shell Scripts') {
            steps {
                sh '''
                echo "=== Basic Environment Check ==="
                echo "Current Directory: $(pwd)"
                echo "Logged-in User: $(whoami)"
                uname -a
                df -h

                echo "=== File Operations Test ==="
                echo "This is a test file for Jenkins job." > testfile.txt
                cat testfile.txt
                mv testfile.txt renamed_testfile.txt
                rm renamed_testfile.txt

                echo "=== Network Connectivity Test ==="
                ping -c 4 google.com
                curl -I https://www.google.com

                echo "=== Build Simulation ==="
                mkdir -p build
                cd build
                touch main.o utils.o program.bin
                ls -la
                cd ..
                rm -rf build
                '''
            }
        }
    }
}
