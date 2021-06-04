# Guide to generate REST API Interface of the adapter

This guide provides information about introducing changes to the REST API Interface. If the any API Level changes are required to be done, it should be added to the `hospitalbackend/resources/backend.yaml`. Then we autogenerate the code from go-swagger tool.

First, You should install the go-swagger in your developer environment.

https://goswagger.io/install.html

Navigate to the `hospitalbackend` directory. Execute the following command. 

```
swagger generate server -t gen -f resources/backend.yaml -t internal/api --exclude-main -A restapi -s restserver
```

Once it is executed, `hospitalbackend/internal/api/restserver` package will be populated. Within the `restserver` directory, there is a file called `configure_restapi.go`. All the code level changes introduced should be included in here. (Authentication logic, additional validations, TLS level configurations etc.)

If you need to have the Main file (for referenece purposes), you should execute the above command without the `--exclude-main` flag.
