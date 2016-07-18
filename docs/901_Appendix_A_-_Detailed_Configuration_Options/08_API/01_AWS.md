#### `api.aws.json` AWS Configuration File
##### `s3` S3 Credentials *- string*
This should contain your AWS S3 Credentials. These will be used by Modules to interface with S3.
```json
	"s3": {
```
###### `bucket` AWS Bucket *- string*
This should contain the bucket where your assets are to be deployed.
```json
		"bucket"  : "our-fancy-project-assets",
```
###### `region` AWS Region *- string*
This should contain the region where your assets are to be deployed.
```json
		"region"  : "eu-west-1",
```
###### `key` AWS API Key *- string*
This should contain your Amazon API Key. This key must have sufficiant permissions granted for accessing the bucket.
```json
		"key"     : "XXXXXXXXXXXXXXXXX",
```
###### `secret` AWS API Secret *- string*
This should contain the other half of your Amazon Credentials. The Amazon API Secret Key that was provided alongside your Amazon API Key. 
```json
		"secret"  : "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```
```
	}
```