# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/projects/v1alpha1/project.proto](#cbws/projects/v1alpha1/project.proto)
    - [Project](#cbws.projects.v1alpha1.Project)
  
- [cbws/projects/v1alpha1/projects.proto](#cbws/projects/v1alpha1/projects.proto)
    - [CreateProjectRequest](#cbws.projects.v1alpha1.CreateProjectRequest)
    - [DeleteProjectMetadata](#cbws.projects.v1alpha1.DeleteProjectMetadata)
    - [DeleteProjectRequest](#cbws.projects.v1alpha1.DeleteProjectRequest)
    - [GetProjectRequest](#cbws.projects.v1alpha1.GetProjectRequest)
    - [ListProjectsRequest](#cbws.projects.v1alpha1.ListProjectsRequest)
    - [ListProjectsResponse](#cbws.projects.v1alpha1.ListProjectsResponse)
  
    - [ProjectsService](#cbws.projects.v1alpha1.ProjectsService)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/projects/v1alpha1/project.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/projects/v1alpha1/project.proto



<a name="cbws.projects.v1alpha1.Project"></a>

### Project



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The name of the project in the format: projects/test-project |
| display_name | [string](#string) |  |  |
| organization | [string](#string) |  | @OutputOnly The id of the project that owns the service account. |
| unique_id | [string](#string) |  | @OutputOnly The UUID of the project |





 

 

 

 



<a name="cbws/projects/v1alpha1/projects.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/projects/v1alpha1/projects.proto



<a name="cbws.projects.v1alpha1.CreateProjectRequest"></a>

### CreateProjectRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  |  |
| name | [string](#string) |  | Required. The name of the project, It is globally unique across CBWS, must be 6-30 characters long, and match the regular expression `[a-z]([-a-z0-9]*[a-z0-9])` to comply with RFC1035. |
| project | [Project](#cbws.projects.v1alpha1.Project) |  | The [Project][cbws.projects.v1alpha1.Project] resource to create. Currently, only the following values are user assignable: `display_name`. |






<a name="cbws.projects.v1alpha1.DeleteProjectMetadata"></a>

### DeleteProjectMetadata







<a name="cbws.projects.v1alpha1.DeleteProjectRequest"></a>

### DeleteProjectRequest
The project delete request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The name of the project in format projects/project-name |






<a name="cbws.projects.v1alpha1.GetProjectRequest"></a>

### GetProjectRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |






<a name="cbws.projects.v1alpha1.ListProjectsRequest"></a>

### ListProjectsRequest
The service account list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| page_size | [int32](#int32) |  | Optional limit on the number of service accounts to include in the response. Further accounts can subsequently be obtained by including the [ListServiceAccountsResponse.next_page_token][google.iam.admin.v1.ListServiceAccountsResponse.next_page_token] in a subsequent request. |
| page_token | [string](#string) |  | Optional pagination token returned in an earlier [ListServiceAccountsResponse.next_page_token][google.iam.admin.v1.ListServiceAccountsResponse.next_page_token]. |






<a name="cbws.projects.v1alpha1.ListProjectsResponse"></a>

### ListProjectsResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| projects | [Project](#cbws.projects.v1alpha1.Project) | repeated |  |
| next_page_token | [string](#string) |  | To retrieve the next page of results, set [ListServiceAccountsRequest.page_token][google.iam.admin.v1.ListServiceAccountsRequest.page_token] to this value. |





 

 

 


<a name="cbws.projects.v1alpha1.ProjectsService"></a>

### ProjectsService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| CreateProject | [CreateProjectRequest](#cbws.projects.v1alpha1.CreateProjectRequest) | [Project](#cbws.projects.v1alpha1.Project) | Create a project, requires the projects.cbws.xyz/Project/create permission on the organization. The principal creating a project will get the owner role on the project. |
| ListProjects | [ListProjectsRequest](#cbws.projects.v1alpha1.ListProjectsRequest) | [ListProjectsResponse](#cbws.projects.v1alpha1.ListProjectsResponse) | List all projects you have access to Requires the projects.cbws.xyz/Project/get permission on the project |
| GetProject | [GetProjectRequest](#cbws.projects.v1alpha1.GetProjectRequest) | [Project](#cbws.projects.v1alpha1.Project) |  |
| DeleteProject | [DeleteProjectRequest](#cbws.projects.v1alpha1.DeleteProjectRequest) | [.google.longrunning.Operation](#google.longrunning.Operation) |  |
| GetPolicy | [.cbws.iam.policy.v1alpha1.GetPolicyRequest](#cbws.iam.policy.v1alpha1.GetPolicyRequest) | [.cbws.iam.policy.v1alpha1.Policy](#cbws.iam.policy.v1alpha1.Policy) | Returns the IAM access control policy for a Project. |
| SetPolicy | [.cbws.iam.policy.v1alpha1.SetPolicyRequest](#cbws.iam.policy.v1alpha1.SetPolicyRequest) | [.cbws.iam.policy.v1alpha1.Policy](#cbws.iam.policy.v1alpha1.Policy) | Sets the IAM access control policy for a Project. |
| TestPermissions | [.cbws.iam.policy.v1alpha1.TestPermissionsRequest](#cbws.iam.policy.v1alpha1.TestPermissionsRequest) | [.cbws.iam.policy.v1alpha1.TestPermissionsResponse](#cbws.iam.policy.v1alpha1.TestPermissionsResponse) | Tests the specified permissions against the IAM access control policy for a Project. |

 



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

