# Issue recreate instructions:

1. Clone
    > git clone git@github.com:scottkurz/ol-env-issue-recreate.git; cd ol-env-issue-recreate

2. Set env vars:
    > export avar=a1 bvar=b1

3. Build and start server
    > mvn package liberty:start

4. Hit the endpoint:
   >  curl -sk https://localhost:9443/ibm/api/config/dataSource/DefaultDataSource -u apps:ody | grep -E '(customProp|serverName)'

and view the output:

    "customProp": "b1",
    "serverName": "a1",

5. Set env vars to new values
    > export avar=a2 bvar=b2

6. Switch to target directory
>  cd target/liberty/wlp/

7. Start server
> ./bin/server start demo

8. Hit the endpoint again

   >  curl -sk https://localhost:9443/ibm/api/config/dataSource/DefaultDataSource -u apps:ody | grep -E '(customProp|serverName)'

and view the output:

    "customProp": "b1",
    "serverName": "a1",

9. Observe this is wrong :) 
