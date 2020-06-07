# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/iam/policy/v1alpha1/policy.proto](#cbws/iam/policy/v1alpha1/policy.proto)
    - [Binding](#cbws.iam.policy.v1alpha1.Binding)
    - [Policy](#cbws.iam.policy.v1alpha1.Policy)
  
- [cbws/iam/policy/v1alpha1/request_response.proto](#cbws/iam/policy/v1alpha1/request_response.proto)
    - [GetPolicyRequest](#cbws.iam.policy.v1alpha1.GetPolicyRequest)
    - [SetPolicyRequest](#cbws.iam.policy.v1alpha1.SetPolicyRequest)
    - [TestPermissionsRequest](#cbws.iam.policy.v1alpha1.TestPermissionsRequest)
    - [TestPermissionsResponse](#cbws.iam.policy.v1alpha1.TestPermissionsResponse)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/iam/policy/v1alpha1/policy.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/iam/policy/v1alpha1/policy.proto



<a name="cbws.iam.policy.v1alpha1.Binding"></a>

### Binding
Associates `members` with a `role`.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| role | [string](#string) |  | Role that is assigned to `members`. For example, `roles/viewer`, `roles/editor`, or `roles/owner`. |
| description | [string](#string) |  |  |
| members | [string](#string) | repeated | Specifies the identities requesting access for a Cloud Platform resource. `members` can have the following values:

* `anonymous`: A special identifier that represents anyone who is on the internet

* `allUsers`: A special identifier that represents anyone who is authenticated with a Cloudbear account or a service account.

* `user:{emailid}`: An email address that represents a specific Google account. For example, `alice@example.com` .

* `serviceAccount:{emailid}`: An email address that represents a service account. For example, `my-other-app@appspot.gserviceaccount.com`.

* `group:{emailid}`: An email address that represents a Google group. For example, `admins@example.com`.

* `principal:{id}`: Identifier of the specific principal, can be used if access to either the user, serviceAccount or group is not available and only the principal id is known. This member type is only available when setting a IAM policy and is not returned when getting a IAM policy. |






<a name="cbws.iam.policy.v1alpha1.Policy"></a>

### Policy
Defines an Identity and Access Management (IAM) policy. It is used to
specify access control policies for Cloud Platform resources.


A `Policy` is a collection of `bindings`. A `binding` binds one or more
`members` to a single `role`. Members can be user accounts, service accounts,
Google groups, and domains (such as G Suite). A `role` is a named list of
permissions (defined by IAM or configured by users). A `binding` can
optionally specify a `condition`, which is a logic expression that further
constrains the role binding based on attributes about the request and/or
target resource.

**JSON Example**

    {
      &#34;bindings&#34;: [
        {
          &#34;role&#34;: &#34;roles/resourcemanager.organizationAdmin&#34;,
          &#34;members&#34;: [
            &#34;user:mike@example.com&#34;,
            &#34;group:admins@example.com&#34;,
            &#34;domain:google.com&#34;,
            &#34;serviceAccount:my-project-id@appspot.gserviceaccount.com&#34;
          ]
        },
        {
          &#34;role&#34;: &#34;roles/resourcemanager.organizationViewer&#34;,
          &#34;members&#34;: [&#34;user:eve@example.com&#34;],
          &#34;condition&#34;: {
            &#34;title&#34;: &#34;expirable access&#34;,
            &#34;description&#34;: &#34;Does not grant access after Sep 2020&#34;,
            &#34;expression&#34;: &#34;request.time &lt;
            timestamp(&#39;2020-10-01T00:00:00.000Z&#39;)&#34;,
          }
        }
      ]
    }

**YAML Example**

    bindings:
    - members:
      - user:mike@example.com
      - group:admins@example.com
      - domain:google.com
      - serviceAccount:my-project-id@appspot.gserviceaccount.com
      role: roles/resourcemanager.organizationAdmin
    - members:
      - user:eve@example.com
      role: roles/resourcemanager.organizationViewer
      condition:
        title: expirable access
        description: Does not grant access after Sep 2020
        expression: request.time &lt; timestamp(&#39;2020-10-01T00:00:00.000Z&#39;)

For a description of IAM and its features, see the
[IAM developer&#39;s guide](https://cloud.google.com/iam/docs).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| bindings | [Binding](#cbws.iam.policy.v1alpha1.Binding) | repeated | Associates a list of `members` to a `role`. Optionally may specify a `condition` that determines when binding is in effect. `bindings` with no members will result in an error. |
| etag | [bytes](#bytes) |  | `etag` is used for optimistic concurrency control as a way to help prevent simultaneous updates of a policy from overwriting each other. It is strongly suggested that systems make use of the `etag` in the read-modify-write cycle to perform policy updates in order to avoid race conditions: An `etag` is returned in the response to `getIamPolicy`, and systems are expected to put that etag in the request to `setIamPolicy` to ensure that their change will be applied to the same version of the policy.

If no `etag` is provided in the call to `setIamPolicy`, then the existing policy is overwritten. Due to blind-set semantics of an etag-less policy, &#39;setIamPolicy&#39; will not fail even if the incoming policy version does not meet the requirements for modifying the stored policy. |





 

 

 

 



<a name="cbws/iam/policy/v1alpha1/request_response.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/iam/policy/v1alpha1/request_response.proto



<a name="cbws.iam.policy.v1alpha1.GetPolicyRequest"></a>

### GetPolicyRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| resource | [string](#string) |  | REQUIRED: The resource for which the policy is being requested. See the operation documentation for the appropriate value for this field. |






<a name="cbws.iam.policy.v1alpha1.SetPolicyRequest"></a>

### SetPolicyRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| resource | [string](#string) |  | REQUIRED: The resource for which the policy is being specified. See the operation documentation for the appropriate value for this field. |
| policy | [Policy](#cbws.iam.policy.v1alpha1.Policy) |  | REQUIRED: The complete policy to be applied to the `resource`. The size of the policy is limited to a few 10s of KB. An empty policy is a valid policy but certain Cloud Platform services (such as Projects) might reject them. |






<a name="cbws.iam.policy.v1alpha1.TestPermissionsRequest"></a>

### TestPermissionsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| resource | [string](#string) |  | REQUIRED: The resource for which the policy detail is being requested. See the operation documentation for the appropriate value for this field. |
| permissions | [string](#string) | repeated | The set of permissions to check for the `resource`. Permissions with wildcards (such as &#39;*&#39; or &#39;storage.*&#39;) are not allowed. For more information see [IAM Overview](https://cloud.google.com/iam/docs/overview#permissions). |






<a name="cbws.iam.policy.v1alpha1.TestPermissionsResponse"></a>

### TestPermissionsResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| permissions | [string](#string) | repeated | A subset of `TestPermissionsRequest.permissions` that the caller is allowed. |





 

 

 

 



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

