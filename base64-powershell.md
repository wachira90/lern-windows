# base64-powershell

## Converting to Base64:
````
[Convert]::ToBase64String([Text.Encoding]::ASCII.GetBytes('Motorhead'))
Output:

TW90b3JoZWFk
````

## Converting from Base64:

````
[Text.Encoding]::ASCII.GetString([Convert]::FromBase64String('TW90b3JoZWFk')) 
Output:

Motorhead
````

## Example Syntax:
````
[Text.Encoding]::Unicode.GetString([System.Convert]::FromBase64String("YmxhaGJsYWg="))
[Text.Encoding]::ASCII.GetString([System.Convert]::FromBase64String("YmxhaGJsYWg="))
````

