# REMOTE RDP COMMAND

## CONNECT_TO_SERVER

````
mstsc /v 172.16.1.50
````

## SPECIFIC_DIMENSION

````
mstsc /v:172.16.1.50 /w:1024 /h:768
````

## FULLSCREEN

````
mstsc /v:172.16.1.50 /f
````

## Span across multiple (2+) monitors

````
mstsc /v:172.16.1.50 /span
````

## The terminal server has exceeded the maximum number of allowed connections

````
mstsc /admin
````

## Create credentials

````
cmdkey /generic:"<servername>" /user:"<username>" /pass:"<password>"
````

## Connect MSTSC with servername and credentials created before

````
mstsc /v:<servername>
````

## Delete the credentials after MSTSC session is done

````
cmdkey /delete:TERMSRV/<servername>
````
