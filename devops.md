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

## 