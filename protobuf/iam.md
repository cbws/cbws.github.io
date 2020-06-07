# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/iam/v1alpha1/iam.proto](#cbws/iam/v1alpha1/iam.proto)
    - [CreateServiceAccountKeyRequest](#cbws.iam.v1alpha1.CreateServiceAccountKeyRequest)
    - [CreateServiceAccountRequest](#cbws.iam.v1alpha1.CreateServiceAccountRequest)
    - [DeleteServiceAccountKeyRequest](#cbws.iam.v1alpha1.DeleteServiceAccountKeyRequest)
    - [DeleteServiceAccountRequest](#cbws.iam.v1alpha1.DeleteServiceAccountRequest)
    - [GenerateAccessTokenRequest](#cbws.iam.v1alpha1.GenerateAccessTokenRequest)
    - [GenerateAccessTokenResponse](#cbws.iam.v1alpha1.GenerateAccessTokenResponse)
    - [GetServiceAccountKeyRequest](#cbws.iam.v1alpha1.GetServiceAccountKeyRequest)
    - [GetServiceAccountRequest](#cbws.iam.v1alpha1.GetServiceAccountRequest)
    - [ListServiceAccountKeysRequest](#cbws.iam.v1alpha1.ListServiceAccountKeysRequest)
    - [ListServiceAccountKeysResponse](#cbws.iam.v1alpha1.ListServiceAccountKeysResponse)
    - [ListServiceAccountsRequest](#cbws.iam.v1alpha1.ListServiceAccountsRequest)
    - [ListServiceAccountsResponse](#cbws.iam.v1alpha1.ListServiceAccountsResponse)
    - [UpdateServiceAccountRequest](#cbws.iam.v1alpha1.UpdateServiceAccountRequest)
  
    - [IAMService](#cbws.iam.v1alpha1.IAMService)
  
- [cbws/iam/v1alpha1/service_account.proto](#cbws/iam/v1alpha1/service_account.proto)
    - [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount)
    - [ServiceAccountKey](#cbws.iam.v1alpha1.ServiceAccountKey)
  
    - [ServiceAccountKeyAlgorithm](#cbws.iam.v1alpha1.ServiceAccountKeyAlgorithm)
    - [ServiceAccountKeyType](#cbws.iam.v1alpha1.ServiceAccountKeyType)
    - [ServiceAccountPrivateKeyType](#cbws.iam.v1alpha1.ServiceAccountPrivateKeyType)
    - [ServiceAccountPublicKeyType](#cbws.iam.v1alpha1.ServiceAccountPublicKeyType)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/iam/v1alpha1/iam.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/iam/v1alpha1/iam.proto



<a name="cbws.iam.v1alpha1.CreateServiceAccountKeyRequest"></a>

### CreateServiceAccountKeyRequest
The service account key create request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the service account in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |
| private_key_type | [ServiceAccountPrivateKeyType](#cbws.iam.v1alpha1.ServiceAccountPrivateKeyType) |  | The output format of the private key. The default value is `TYPE_GOOGLE_CREDENTIALS_FILE`, which is the Google Credentials File format. |
| key_algorithm | [ServiceAccountKeyAlgorithm](#cbws.iam.v1alpha1.ServiceAccountKeyAlgorithm) |  | Which type of key and algorithm to use for the key. The default is currently a 2K RSA key. However this may change in the future. |






<a name="cbws.iam.v1alpha1.CreateServiceAccountRequest"></a>

### CreateServiceAccountRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the service accounts, such as `projects/my-project-123`. |
| account_id | [string](#string) |  | Required. The account id that is used to generate the service account email address and a stable unique id. It is unique within a project, must be 6-30 characters long, and match the regular expression `[a-z]([-a-z0-9]*[a-z0-9])` to comply with RFC1035. |
| service_account | [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount) |  | The [ServiceAccount][google.iam.admin.v1.ServiceAccount] resource to create. Currently, only the following values are user assignable: `display_name` and `description`. |






<a name="cbws.iam.v1alpha1.DeleteServiceAccountKeyRequest"></a>

### DeleteServiceAccountKeyRequest
The service account key delete request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the service account key in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}/keys/{key}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |






<a name="cbws.iam.v1alpha1.DeleteServiceAccountRequest"></a>

### DeleteServiceAccountRequest
The service account delete request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the service account in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |






<a name="cbws.iam.v1alpha1.GenerateAccessTokenRequest"></a>

### GenerateAccessTokenRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the service account in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |
| delegates | [string](#string) | repeated | The sequence of service accounts in a delegation chain. Each service account must be granted the `roles/iam.serviceAccountTokenCreator` role on its next service account in the chain. The last service account in the chain must be granted the `roles/iam.serviceAccountTokenCreator` role on the service account that is specified in the `name` field of the request.

The delegates must have the following format: `projects/-/serviceAccounts/{ACCOUNT_EMAIL_OR_UNIQUEID}`. The `-` wildcard character is required; replacing it with a project ID is invalid. |
| scope | [string](#string) | repeated | Required. Code to identify the scopes to be included in the OAuth 2.0 access token. See https://developers.google.com/identity/protocols/googlescopes for more information. At least one value required. |
| lifetime | [google.protobuf.Duration](#google.protobuf.Duration) |  | The desired lifetime duration of the access token in seconds. Must be set to a value less than or equal to 3600 (1 hour). If a value is not specified, the token&#39;s lifetime will be set to a default value of one hour. |






<a name="cbws.iam.v1alpha1.GenerateAccessTokenResponse"></a>

### GenerateAccessTokenResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| access_token | [string](#string) |  | The OAuth 2.0 access token. |
| expire_time | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  | Token expiration time. The expiration time is always set. |






<a name="cbws.iam.v1alpha1.GetServiceAccountKeyRequest"></a>

### GetServiceAccountKeyRequest
The service account key get by id request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the service account key in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}/keys/{key}`.

Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |
| public_key_type | [ServiceAccountPublicKeyType](#cbws.iam.v1alpha1.ServiceAccountPublicKeyType) |  | The output format of the public key requested. X509_PEM is the default output format. |






<a name="cbws.iam.v1alpha1.GetServiceAccountRequest"></a>

### GetServiceAccountRequest
The service account get request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the service account in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |






<a name="cbws.iam.v1alpha1.ListServiceAccountKeysRequest"></a>

### ListServiceAccountKeysRequest
The service account keys list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the service account in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`.

Using `-` as a wildcard for the `PROJECT_ID`, will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the service account. |
| key_types | [ServiceAccountKeyType](#cbws.iam.v1alpha1.ServiceAccountKeyType) | repeated | Filters the types of keys the user wants to include in the list response. Duplicate key types are not allowed. If no key type is provided, all keys are returned. |






<a name="cbws.iam.v1alpha1.ListServiceAccountKeysResponse"></a>

### ListServiceAccountKeysResponse
The service account keys list response.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| keys | [ServiceAccountKey](#cbws.iam.v1alpha1.ServiceAccountKey) | repeated | The public keys for the service account. |






<a name="cbws.iam.v1alpha1.ListServiceAccountsRequest"></a>

### ListServiceAccountsRequest
The service account list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the service accounts, such as `projects/my-project-123`. |
| page_size | [int32](#int32) |  | Optional limit on the number of service accounts to include in the response. Further accounts can subsequently be obtained by including the [ListServiceAccountsResponse.next_page_token][google.iam.admin.v1.ListServiceAccountsResponse.next_page_token] in a subsequent request. |
| page_token | [string](#string) |  | Optional pagination token returned in an earlier [ListServiceAccountsResponse.next_page_token][google.iam.admin.v1.ListServiceAccountsResponse.next_page_token]. |






<a name="cbws.iam.v1alpha1.ListServiceAccountsResponse"></a>

### ListServiceAccountsResponse
The service account list response.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| accounts | [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount) | repeated | The list of matching service accounts. |
| next_page_token | [string](#string) |  | To retrieve the next page of results, set [ListServiceAccountsRequest.page_token][google.iam.admin.v1.ListServiceAccountsRequest.page_token] to this value. |






<a name="cbws.iam.v1alpha1.UpdateServiceAccountRequest"></a>

### UpdateServiceAccountRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| service_account | [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount) |  | The [ServiceAccount][google.iam.admin.v1.ServiceAccount] resource to create. Currently, only the following values are user assignable: `display_name` and `description`. |





 

 

 


<a name="cbws.iam.v1alpha1.IAMService"></a>

### IAMService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ListServiceAccounts | [ListServiceAccountsRequest](#cbws.iam.v1alpha1.ListServiceAccountsRequest) | [ListServiceAccountsResponse](#cbws.iam.v1alpha1.ListServiceAccountsResponse) |  |
| GetServiceAccount | [GetServiceAccountRequest](#cbws.iam.v1alpha1.GetServiceAccountRequest) | [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount) |  |
| CreateServiceAccount | [CreateServiceAccountRequest](#cbws.iam.v1alpha1.CreateServiceAccountRequest) | [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount) |  |
| UpdateServiceAccount | [UpdateServiceAccountRequest](#cbws.iam.v1alpha1.UpdateServiceAccountRequest) | [ServiceAccount](#cbws.iam.v1alpha1.ServiceAccount) |  |
| DeleteServiceAccount | [DeleteServiceAccountRequest](#cbws.iam.v1alpha1.DeleteServiceAccountRequest) | [.google.protobuf.Empty](#google.protobuf.Empty) | Deletes a [ServiceAccount][google.iam.admin.v1.ServiceAccount]. |
| GenerateAccessToken | [GenerateAccessTokenRequest](#cbws.iam.v1alpha1.GenerateAccessTokenRequest) | [GenerateAccessTokenResponse](#cbws.iam.v1alpha1.GenerateAccessTokenResponse) | Generates an OAuth 2.0 access token for a service account. |
| ListServiceAccountKeys | [ListServiceAccountKeysRequest](#cbws.iam.v1alpha1.ListServiceAccountKeysRequest) | [ListServiceAccountKeysResponse](#cbws.iam.v1alpha1.ListServiceAccountKeysResponse) | Lists [ServiceAccountKeys][google.iam.admin.v1.ServiceAccountKey]. |
| GetServiceAccountKey | [GetServiceAccountKeyRequest](#cbws.iam.v1alpha1.GetServiceAccountKeyRequest) | [ServiceAccountKey](#cbws.iam.v1alpha1.ServiceAccountKey) | Gets the [ServiceAccountKey][google.iam.admin.v1.ServiceAccountKey] by key id. |
| CreateServiceAccountKey | [CreateServiceAccountKeyRequest](#cbws.iam.v1alpha1.CreateServiceAccountKeyRequest) | [ServiceAccountKey](#cbws.iam.v1alpha1.ServiceAccountKey) | Creates a [ServiceAccountKey][google.iam.admin.v1.ServiceAccountKey] and returns it. |
| DeleteServiceAccountKey | [DeleteServiceAccountKeyRequest](#cbws.iam.v1alpha1.DeleteServiceAccountKeyRequest) | [.google.protobuf.Empty](#google.protobuf.Empty) | Deletes a [ServiceAccountKey][google.iam.admin.v1.ServiceAccountKey]. |
| GetPolicy | [.cbws.iam.policy.v1alpha1.GetPolicyRequest](#cbws.iam.policy.v1alpha1.GetPolicyRequest) | [.cbws.iam.policy.v1alpha1.Policy](#cbws.iam.policy.v1alpha1.Policy) | Returns the Cloud IAM access control policy for a [ServiceAccount][google.iam.admin.v1.ServiceAccount].

Note: Service accounts are both [resources and identities](/iam/docs/service-accounts#service_account_permissions). This method treats the service account as a resource. It returns the Cloud IAM policy that reflects what members have access to the service account.

This method does not return what resources the service account has access to. To see if a service account has access to a resource, call the `getIamPolicy` method on the target resource. For example, to view grants for a project, call the [projects.getIamPolicy](/resource-manager/reference/rest/v1/projects/getIamPolicy) method. |
| SetPolicy | [.cbws.iam.policy.v1alpha1.SetPolicyRequest](#cbws.iam.policy.v1alpha1.SetPolicyRequest) | [.cbws.iam.policy.v1alpha1.Policy](#cbws.iam.policy.v1alpha1.Policy) | Sets the Cloud IAM access control policy for a [ServiceAccount][google.iam.admin.v1.ServiceAccount].

Note: Service accounts are both [resources and identities](/iam/docs/service-accounts#service_account_permissions). This method treats the service account as a resource. Use it to grant members access to the service account, such as when they need to impersonate it.

This method does not grant the service account access to other resources, such as projects. To grant a service account access to resources, include the service account in the Cloud IAM policy for the desired resource, then call the appropriate `setIamPolicy` method on the target resource. For example, to grant a service account access to a project, call the [projects.setIamPolicy](/resource-manager/reference/rest/v1/projects/setIamPolicy) method. |

 



<a name="cbws/iam/v1alpha1/service_account.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/iam/v1alpha1/service_account.proto



<a name="cbws.iam.v1alpha1.ServiceAccount"></a>

### ServiceAccount



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The resource name of the service account in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`.

Requests using `-` as a wildcard for the `PROJECT_ID` will infer the project from the `account` and the `ACCOUNT` value can be the `email` address or the `unique_id` of the service account.

In responses the resource name will always be in the format `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. |
| project_id | [string](#string) |  | @OutputOnly The id of the project that owns the service account. |
| unique_id | [string](#string) |  | @OutputOnly The unique and stable id of the service account. |
| email | [string](#string) |  | @OutputOnly The email address of the service account. |
| display_name | [string](#string) |  | Optional. A user-specified name for the service account. Must be less than or equal to 100 UTF-8 bytes. |






<a name="cbws.iam.v1alpha1.ServiceAccountKey"></a>

### ServiceAccountKey
Represents a service account key.

A service account has two sets of key-pairs: user-managed, and
system-managed.

User-managed key-pairs can be created and deleted by users.  Users are
responsible for rotating these keys periodically to ensure security of
their service accounts.  Users retain the private key of these key-pairs,
and Cloudbear retains ONLY the public key.

System-managed keys are automatically rotated by Cloudbear, and are used for
signing for a maximum of two weeks. The rotation process is probabilistic,
and usage of the new key will gradually ramp up and down over the key&#39;s
lifetime. We recommend caching the public key set for a service account for
no more than 24 hours to ensure you have access to the latest keys.

Public keys for all service accounts are also published at the OAuth2
Service Account API.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The resource name of the service account key in the following format `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}/keys/{key}`. |
| key_type | [ServiceAccountKeyType](#cbws.iam.v1alpha1.ServiceAccountKeyType) |  |  |
| private_key_type | [ServiceAccountPrivateKeyType](#cbws.iam.v1alpha1.ServiceAccountPrivateKeyType) |  | The output format for the private key. Only provided in `CreateServiceAccountKey` responses, not in `GetServiceAccountKey` or `ListServiceAccountKey` responses.

Cloudbear never exposes system-managed private keys, and never retains user-managed private keys. |
| key_algorithm | [ServiceAccountKeyAlgorithm](#cbws.iam.v1alpha1.ServiceAccountKeyAlgorithm) |  | Specifies the algorithm (and possibly key size) for the key. |
| private_key_data | [bytes](#bytes) |  | The private key data. Only provided in `CreateServiceAccountKey` responses. Make sure to keep the private key data secure because it allows for the assertion of the service account identity. When base64 decoded, the private key data can be used to authenticate with Cloudbear API client libraries and with &lt;a href=&#34;/sdk/gcloud/reference/auth/activate-service-account&#34;&gt;gcloud auth activate-service-account&lt;/a&gt;. |
| public_key_data | [bytes](#bytes) |  | The public key data. Only provided in `GetServiceAccountKey` responses. |
| valid_after_time | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  | The key can be used after this timestamp. |
| valid_before_time | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  | The key can be used before this timestamp. For system-managed key pairs, this timestamp is the end time for the private key signing operation. The public key could still be used for verification for a few hours after this time. |





 


<a name="cbws.iam.v1alpha1.ServiceAccountKeyAlgorithm"></a>

### ServiceAccountKeyAlgorithm
Supported key algorithms.

| Name | Number | Description |
| ---- | ------ | ----------- |
| SERVICE_ACCOUNT_KEY_ALGORITHM_UNSPECIFIED | 0 | An unspecified key algorithm. |
| SERVICE_ACCOUNT_KEY_ALGORITHM_RSA_1024 | 1 | 1k RSA Key. |
| SERVICE_ACCOUNT_KEY_ALGORITHM_RSA_2048 | 2 | 2k RSA Key. |
| SERVICE_ACCOUNT_KEY_ALGORITHM_RSA_4096 | 3 | 4k RSA Key. |



<a name="cbws.iam.v1alpha1.ServiceAccountKeyType"></a>

### ServiceAccountKeyType


| Name | Number | Description |
| ---- | ------ | ----------- |
| SERVICE_ACCOUNT_KEY_TYPE_UNSPECIFIED | 0 | Unspecified key type. The presence of this in the message will immediately result in an error. |
| SERVICE_ACCOUNT_KEY_TYPE_USER_MANAGED | 1 | User-managed keys (managed and rotated by the user). |
| SERVICE_ACCOUNT_KEY_TYPE_SYSTEM_MANAGED | 2 | System-managed keys (managed and rotated by Cloudbear). |



<a name="cbws.iam.v1alpha1.ServiceAccountPrivateKeyType"></a>

### ServiceAccountPrivateKeyType
Supported private key output formats.

| Name | Number | Description |
| ---- | ------ | ----------- |
| SERVICE_ACCOUNT_PRIVATE_KEY_TYPE_UNSPECIFIED | 0 | Unspecified. Equivalent to `TYPE_CREDENTIALS_FILE`. |
| SERVICE_ACCOUNT_PRIVATE_KEY_TYPE_PKCS12_FILE | 1 | PKCS12 format. The password for the PKCS12 file is `notasecret`. For more information, see https://tools.ietf.org/html/rfc7292. |
| SERVICE_ACCOUNT_PRIVATE_KEY_TYPE_CREDENTIALS_FILE | 2 | Credentials File format. |



<a name="cbws.iam.v1alpha1.ServiceAccountPublicKeyType"></a>

### ServiceAccountPublicKeyType
Supported public key output formats.

| Name | Number | Description |
| ---- | ------ | ----------- |
| SERVICE_ACCOUNT_PUBLIC_KEY_TYPE_UNSPECIFIED | 0 | Unspecified. Returns nothing here. |
| SERVICE_ACCOUNT_PUBLIC_KEY_TYPE_X509_PEM_FILE | 1 | X509 PEM format. |
| SERVICE_ACCOUNT_PUBLIC_KEY_TYPE_PKCS8_PUBLIC_KEY | 2 | PKCS #8 public key. |


 

 

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

