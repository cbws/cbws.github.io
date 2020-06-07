# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/vpn/v1alpha1/instance.proto](#cbws/vpn/v1alpha1/instance.proto)
    - [Instance](#cbws.vpn.v1alpha1.Instance)
    - [Profile](#cbws.vpn.v1alpha1.Profile)
  
- [cbws/vpn/v1alpha1/vpn.proto](#cbws/vpn/v1alpha1/vpn.proto)
    - [CreateInstanceRequest](#cbws.vpn.v1alpha1.CreateInstanceRequest)
    - [CreateProfileRequest](#cbws.vpn.v1alpha1.CreateProfileRequest)
    - [DeleteInstanceRequest](#cbws.vpn.v1alpha1.DeleteInstanceRequest)
    - [DeleteProfileRequest](#cbws.vpn.v1alpha1.DeleteProfileRequest)
    - [GetInstanceRequest](#cbws.vpn.v1alpha1.GetInstanceRequest)
    - [GetProfileRequest](#cbws.vpn.v1alpha1.GetProfileRequest)
    - [ListInstancesRequest](#cbws.vpn.v1alpha1.ListInstancesRequest)
    - [ListInstancesResponse](#cbws.vpn.v1alpha1.ListInstancesResponse)
    - [ListProfilesRequest](#cbws.vpn.v1alpha1.ListProfilesRequest)
    - [ListProfilesResponse](#cbws.vpn.v1alpha1.ListProfilesResponse)
    - [UpdateInstanceRequest](#cbws.vpn.v1alpha1.UpdateInstanceRequest)
    - [UpdateProfileRequest](#cbws.vpn.v1alpha1.UpdateProfileRequest)
  
    - [VPNService](#cbws.vpn.v1alpha1.VPNService)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/vpn/v1alpha1/instance.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/vpn/v1alpha1/instance.proto



<a name="cbws.vpn.v1alpha1.Instance"></a>

### Instance



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |
| parent | [string](#string) |  |  |
| display_name | [string](#string) |  |  |
| ipv6_prefix | [string](#string) |  | The IPv6 prefix from which profile addresses will be allocated |
| ipv6_default_gateway | [bool](#bool) |  | Whether to make the VPN the default IPv6 gateway on profile clients |
| ipv4_default_gateway | [bool](#bool) |  | Whether to make the VPN the default IPv4 gateway on profile clients This is not recommended and only included for completeness and specific use-cases. IPv6 should be used for accessing private services whenever possible. |






<a name="cbws.vpn.v1alpha1.Profile"></a>

### Profile



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  |  |
| parent | [string](#string) |  |  |
| display_name | [string](#string) |  |  |
| ipv6_prefix | [string](#string) |  | The IPv6 prefix that gets routed to the profile client Read-only |
| ipv6_address | [string](#string) |  | The IPv6 address assigned to the profile client Read-only |
| ipv6_gateway_address | [string](#string) |  | The IPv6 remote peer address that gets send to the profile client Read-only |
| ipv4_464xlat_address | [string](#string) |  | The IPv6 address used as source for translated IPv4 packets Read-only |
| ipv4_address | [string](#string) |  | The IPv4 address assigned to the profile client Read-only |
| ipv4_gateway_address | [string](#string) |  | The IPv4 remote peer address that gets send to the profile client Read-only |
| profile_archive | [bytes](#bytes) |  | A ZIP archive containing the certificates and OpenVPN profile. Only available during create |
| ca_certificate | [string](#string) |  | The CA certificate for the client and server certificate. Only available during create |
| certificate | [string](#string) |  | The certificate to be used by the client. Only available during create |
| private_key | [string](#string) |  | The private key to be used by the client. Only available during create |





 

 

 

 



<a name="cbws/vpn/v1alpha1/vpn.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/vpn/v1alpha1/vpn.proto



<a name="cbws.vpn.v1alpha1.CreateInstanceRequest"></a>

### CreateInstanceRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the service accounts, such as `projects/my-project-123`. |
| name | [string](#string) |  | Required. The name of the instance, without the projects prefix |
| instance | [Instance](#cbws.vpn.v1alpha1.Instance) |  | The [Instance][cbws.vpn.v1alpha1.Instance] resource to create. Currently, only the following values are user assignable: `display_name` and `description`. |






<a name="cbws.vpn.v1alpha1.CreateProfileRequest"></a>

### CreateProfileRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the service accounts, such as `projects/my-project-123`. |
| name | [string](#string) |  | Required. The name of the instance, without the projects prefix |
| profile | [Profile](#cbws.vpn.v1alpha1.Profile) |  | The [Instance][cbws.vpn.v1alpha1.Instance] resource to create. Currently, only the following values are user assignable: `display_name` and `description`. |






<a name="cbws.vpn.v1alpha1.DeleteInstanceRequest"></a>

### DeleteInstanceRequest
The instance delete request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the instance in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the instance. |






<a name="cbws.vpn.v1alpha1.DeleteProfileRequest"></a>

### DeleteProfileRequest
The instance delete request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the instance in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the instance. |






<a name="cbws.vpn.v1alpha1.GetInstanceRequest"></a>

### GetInstanceRequest
The instance get request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the instance in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the instance. |






<a name="cbws.vpn.v1alpha1.GetProfileRequest"></a>

### GetProfileRequest
The instance get request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the instance in the following format: `projects/{PROJECT_ID}/serviceAccounts/{ACCOUNT}`. Using `-` as a wildcard for the `PROJECT_ID` will infer the project from the account. The `ACCOUNT` value can be the `email` address or the `unique_id` of the instance. |






<a name="cbws.vpn.v1alpha1.ListInstancesRequest"></a>

### ListInstancesRequest
The instance list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the service accounts, such as `projects/my-project-123`. |
| page_size | [int32](#int32) |  | Optional limit on the number of instances to include in the response. Further accounts can subsequently be obtained by including the [ListInstancesResponse.next_page_token][cbws.vpn.v1alpha1.ListInstancesResponse.next_page_token] in a subsequent request. |
| page_token | [string](#string) |  | Optional pagination token returned in an earlier [ListInstancesResponse.next_page_token][cbws.vpn.v1alpha1.ListInstancesResponse.next_page_token]. |






<a name="cbws.vpn.v1alpha1.ListInstancesResponse"></a>

### ListInstancesResponse
The instance list response.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| instances | [Instance](#cbws.vpn.v1alpha1.Instance) | repeated | The list of matching instances. |
| next_page_token | [string](#string) |  | To retrieve the next page of results, set [ListInstancesRequest.page_token][cbws.vpn.v1alpha1.ListInstancesRequest.page_token] to this value. |






<a name="cbws.vpn.v1alpha1.ListProfilesRequest"></a>

### ListProfilesRequest
The instance list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  |  |
| page_size | [int32](#int32) |  | Optional limit on the number of instances to include in the response. Further accounts can subsequently be obtained by including the [ListInstancesResponse.next_page_token][cbws.vpn.v1alpha1.ListInstancesResponse.next_page_token] in a subsequent request. |
| page_token | [string](#string) |  | Optional pagination token returned in an earlier [ListInstancesResponse.next_page_token][cbws.vpn.v1alpha1.ListInstancesResponse.next_page_token]. |






<a name="cbws.vpn.v1alpha1.ListProfilesResponse"></a>

### ListProfilesResponse
The instance list response.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| profiles | [Profile](#cbws.vpn.v1alpha1.Profile) | repeated | The list of matching profiles. |
| next_page_token | [string](#string) |  | To retrieve the next page of results, set [ListInstancesRequest.page_token][cbws.vpn.v1alpha1.ListInstancesRequest.page_token] to this value. |






<a name="cbws.vpn.v1alpha1.UpdateInstanceRequest"></a>

### UpdateInstanceRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| instance | [Instance](#cbws.vpn.v1alpha1.Instance) |  | The [Instance][cbws.vpn.v1alpha1.Instance] resource to create. Currently, only the following values are user assignable: `display_name` and `description`. |






<a name="cbws.vpn.v1alpha1.UpdateProfileRequest"></a>

### UpdateProfileRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| profile | [Profile](#cbws.vpn.v1alpha1.Profile) |  | The [Profile][cbws.vpn.v1alpha1.Instance] resource to create. Currently, only the following values are user assignable: `display_name` and `description`. |





 

 

 


<a name="cbws.vpn.v1alpha1.VPNService"></a>

### VPNService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ListInstances | [ListInstancesRequest](#cbws.vpn.v1alpha1.ListInstancesRequest) | [ListInstancesResponse](#cbws.vpn.v1alpha1.ListInstancesResponse) |  |
| GetInstance | [GetInstanceRequest](#cbws.vpn.v1alpha1.GetInstanceRequest) | [Instance](#cbws.vpn.v1alpha1.Instance) |  |
| CreateInstance | [CreateInstanceRequest](#cbws.vpn.v1alpha1.CreateInstanceRequest) | [Instance](#cbws.vpn.v1alpha1.Instance) |  |
| UpdateInstance | [UpdateInstanceRequest](#cbws.vpn.v1alpha1.UpdateInstanceRequest) | [Instance](#cbws.vpn.v1alpha1.Instance) |  |
| DeleteInstance | [DeleteInstanceRequest](#cbws.vpn.v1alpha1.DeleteInstanceRequest) | [.google.protobuf.Empty](#google.protobuf.Empty) | Deletes a VPN instance |
| ListProfiles | [ListProfilesRequest](#cbws.vpn.v1alpha1.ListProfilesRequest) | [ListProfilesResponse](#cbws.vpn.v1alpha1.ListProfilesResponse) |  |
| GetProfile | [GetProfileRequest](#cbws.vpn.v1alpha1.GetProfileRequest) | [Profile](#cbws.vpn.v1alpha1.Profile) |  |
| CreateProfile | [CreateProfileRequest](#cbws.vpn.v1alpha1.CreateProfileRequest) | [Profile](#cbws.vpn.v1alpha1.Profile) |  |
| UpdateProfile | [UpdateProfileRequest](#cbws.vpn.v1alpha1.UpdateProfileRequest) | [Profile](#cbws.vpn.v1alpha1.Profile) |  |
| DeleteProfile | [DeleteProfileRequest](#cbws.vpn.v1alpha1.DeleteProfileRequest) | [.google.protobuf.Empty](#google.protobuf.Empty) | Deletes a VPN profile. |

 



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

