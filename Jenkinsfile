node {
    stage('Build'){
        agent{
            docker{
                image 'python:2-alpine'
            }
        }
        step{
            sh "python -m py.compile sources/addvals.py source/calc.py"
        }
    }
    stage('Test'){
        agent{
            docker{
                image 'qnib/pytest'
            }
        }
        step{
            sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
        }
        post{
            always{
                junit 'test-report/result.xml'
            }
        }
    }
}