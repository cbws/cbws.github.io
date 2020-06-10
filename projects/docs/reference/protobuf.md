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
| GetPolicy | [.cbws.iam.policy.v1alpha1.GetPolicyRequest](#cbws.iam.policy.v1alpha1.GetPolicyRequest) | [.cbws.iam.policy.v1alpha1.Policy](#cbws.iam.policy.v1alpha1.Policy) | Returns the IAM access control policy for a Project. |
| SetPolicy | [.cbws.iam.policy.v1alpha1.SetPolicyRequest](#cbws.iam.policy.v1alpha1.SetPolicyRequest) | [.cbws.iam.policy.v1alpha1.Policy](#cbws.iam.policy.v1alpha1.Policy) | Sets the IAM access control policy for a Project. |
| TestPermissions | [.cbws.iam.policy.v1alpha1.TestPermissionsRequest](#cbws.iam.policy.v1alpha1.TestPermissionsRequest) | [.cbws.iam.policy.v1alpha1.TestPermissionsResponse](#cbws.iam.policy.v1alpha1.TestPermissionsResponse) | Tests the specified permissions against the IAM access control policy for a Project. |
