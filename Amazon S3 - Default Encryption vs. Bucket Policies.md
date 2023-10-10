- automatically applied to new objects stored in S3 bucket
- force encryption using bucket policy to refuse any API calls to PUT an S3 object without encryption headers (SSE-KMS or SSE-C)

``"StringNotEquals: {
		"s3:x-amz-server-side-encryption": "aws:kms"
	}"``
``"Null: {
		"s3:x-amz-server-side-encryption-customer-algorithm": "true"
	}"``

🔑 *Note*: Bucket Policies are evaluated before "Default Encryption"

