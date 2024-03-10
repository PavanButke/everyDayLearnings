## before deploying
check if application is in running state
1. `go build main.go`
2. `go test`
3. `go run`

## deployment flow
GIT(Src Code) --> CI/CD (jenkins) --> 1. Build 
                                      2. Unit Test
                                      3. Security
                                      4. E2e Test
                                      5. Deploy

## git
setup a branch of git for jenkins deployment
--> main/master 

## jenkins
1. check if jenkins is running on 8443
2. creating new pipeline
    - new item -> Pipeline -> click ok -> create
        - name: app-ci-cd
            - select "Pipeline"
                  - define as : Pipeline script from SCM 
                - (if having multiple master node : agent node1 or agent  node2)
                - if have single master node : agent any
                - stage : Build
                  -  steps : Add build step -> Invoke top level
                     -  write `stage('Build'){
                     -  {
                            //steps  
                     -  }}`
                     -  git branch url
                  - OR if you want to generate grooy script automatically
                    - Pipeline Syntax
                      - Select option -> git:Git
                      - Repository URL
                      - Git Branch -> Master/Main/Other
                      - Click Button --> Generate Pipeline Script
                    - `sh "go build main.go"`
                      -  OR  use  Pipeline Syntax
                         -   Select option -> sh: Shell script
                         -   Shell script -> `go build main.go`
                         -   copy command 
                - Stage : Test
                   -steps : Add Test step -> Invoke top level
                     -  write `stage('Test'){
                     -  {
                            //steps  
                     -  }}`
                      -   Select option -> sh: Shell script
                         -   Shell script -> `go test`
                         -   copy command
                      - Paste instead of //steps
  
                - Stage : Deploy
                   -steps : Add Test step -> 
                     -  write `stage('Deploy/Run'){
                     -  {
                            //steps  
                     -  }}`
                      -   Select option -> sh: Shell script
                         -   Shell script -> `nohup go run main.go 2>&1 &`
                         -   copy command
                      - Paste instead of //steps 
                    - 
        - Save the file and click on the play button in the upper right corner to start a new pipeline
            - 