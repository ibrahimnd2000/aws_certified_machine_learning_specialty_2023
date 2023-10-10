
- 4 methods

1. SSE
	1. SSE-S3 (Default)
	2. SSE-KMS
	3. SSE-C
2. Client-Side Encryption

#### Amazon S3 Encryption - SSE-S3
- Keys handled and managed by AWS
- Encrypted server side
- Type is AES-256
- header `x-amz-server-side-encryption: AES256`
- Enabled by default for new buckets & new objects

#### Amazon S3 Encryption - SSE-KMS
- managed by AWS
- more user control + audit key using cloudtrail
- header `x-amz-server-side-encryption: aws:kms

##### Limitations:
- Impact from KMS limits
- GenerateDataKey KMS API
- Decrypt KMS API
- KMS Quota
- increase quota using service quotas console.
#### Amazon S3 Encryption - SSE-C
- Managed by customers
- Does Not store the encryption
- HTTPS must be used
- must pass by headers

#### Client-Side Encryption
- client libraries
- must encrypt and decrypt data
- fully managed by customers

#### Amazon S3 - Encryption in transit (SSL/TLS)

- Encryption in flight is also called SSL/TLS
- S3 exposes:
	- HTTP endpoint
	- HTTPS endpoint
- HTTPS is recommended
- mandatory for SSE-C

#### Amazon S3 - Force Encryption in Transit aws:SecureTransport:

- using bucket policy

```
	"Condition": {
		"Bool": {
			"aws:SecureTransport": "false"
		}
	}
```

DKMS - Dual KMS with Matte

Bucket Key - to reduce the cost by reducing API calls to AWS KMS

SSE-C only from CLI

For client-side you don't have set anything.

