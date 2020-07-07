# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/service_management/resource_accounting/v1alpha1/resource_accounting.proto](#cbws/service_management/resource_accounting/v1alpha1/resource_accounting.proto)
    - [AccountRequest](#cbws.service_management.resource_accounting.v1alpha1.AccountRequest)
    - [AccountResponse](#cbws.service_management.resource_accounting.v1alpha1.AccountResponse)
    - [ListResourcesRequest](#cbws.service_management.resource_accounting.v1alpha1.ListResourcesRequest)
    - [ListResourcesResponse](#cbws.service_management.resource_accounting.v1alpha1.ListResourcesResponse)
    - [Resource](#cbws.service_management.resource_accounting.v1alpha1.Resource)
    - [Usage](#cbws.service_management.resource_accounting.v1alpha1.Usage)
    - [UsageCurrent](#cbws.service_management.resource_accounting.v1alpha1.UsageCurrent)
    - [UsageDelta](#cbws.service_management.resource_accounting.v1alpha1.UsageDelta)
    - [UsageTotal](#cbws.service_management.resource_accounting.v1alpha1.UsageTotal)
  
    - [ResourceAccountingService](#cbws.service_management.resource_accounting.v1alpha1.ResourceAccountingService)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/service_management/resource_accounting/v1alpha1/resource_accounting.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/service_management/resource_accounting/v1alpha1/resource_accounting.proto



<a name="cbws.service_management.resource_accounting.v1alpha1.AccountRequest"></a>

### AccountRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| service | [string](#string) |  | The service resource name in the format of services/vm.cbws.xyz |
| consumer_project | [string](#string) |  | The project resource name in the format of projects/project-name |
| resource | [string](#string) |  | The resource to account usage for in format of //service.cbws.xyz/resource-name |
| resource_display_name | [string](#string) |  | The display name to be shown in UIs and on resource accounting documents. The display name will be updated to the last updated value. |
| usage | [Usage](#cbws.service_management.resource_accounting.v1alpha1.Usage) | repeated | All the usages to report by product |






<a name="cbws.service_management.resource_accounting.v1alpha1.AccountResponse"></a>

### AccountResponse







<a name="cbws.service_management.resource_accounting.v1alpha1.ListResourcesRequest"></a>

### ListResourcesRequest
The resource list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the resource, such as `projects/my-project-123`. |
| page_size | [int32](#int32) |  | Optional limit on the number of resources to include in the response. Further resources can subsequently be obtained by including the next_page_token in a subsequent request. |
| page_token | [string](#string) |  | Optional pagination token returned in an earlier next_page_token. |






<a name="cbws.service_management.resource_accounting.v1alpha1.ListResourcesResponse"></a>

### ListResourcesResponse
The resource list response.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| resources | [Resource](#cbws.service_management.resource_accounting.v1alpha1.Resource) | repeated | The list of matching resources. |
| next_page_token | [string](#string) |  | To retrieve the next page of results, set ListResourcesRequest to this value. |






<a name="cbws.service_management.resource_accounting.v1alpha1.Resource"></a>

### Resource



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The full resource name of the resource in the format of projects/project-name/resources/iam.cbws.xyz/projects/project-name/serviceAccounts/iam@iam |
| parent | [string](#string) |  | The project name of this resource |
| display_name | [string](#string) |  | The display name of this resource |






<a name="cbws.service_management.resource_accounting.v1alpha1.Usage"></a>

### Usage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| product | [string](#string) |  | The product resource name in format services/domains.cbws.xyz/products/domain-nl |
| total | [UsageTotal](#cbws.service_management.resource_accounting.v1alpha1.UsageTotal) |  | Report the latest total usage of a particular product

This is useful where you only know the latest value, like kWh power usage read from powerbars. |
| delta | [UsageDelta](#cbws.service_management.resource_accounting.v1alpha1.UsageDelta) |  | Report the new usage since the latest accounting request of a particular product

This is useful when you want to report complexity of an API call, report the renewal/registration of a domain name or other one of actions. |
| current | [UsageCurrent](#cbws.service_management.resource_accounting.v1alpha1.UsageCurrent) |  | Report the current resource usage per period of a particular product this will automatically calculate the delta since the last accounting request

This is useful for services that have constant usage like virtual machines, you can simply report that the current usage is 4 CPUs, 8 GB of RAM and 20 GB of SSD. |






<a name="cbws.service_management.resource_accounting.v1alpha1.UsageCurrent"></a>

### UsageCurrent



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| usage | [double](#double) |  |  |






<a name="cbws.service_management.resource_accounting.v1alpha1.UsageDelta"></a>

### UsageDelta



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| delta | [double](#double) |  |  |






<a name="cbws.service_management.resource_accounting.v1alpha1.UsageTotal"></a>

### UsageTotal



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| current_total | [double](#double) |  | The current total value of usage |





 

 

 


<a name="cbws.service_management.resource_accounting.v1alpha1.ResourceAccountingService"></a>

### ResourceAccountingService
This service is meant to be used by service owners and can be used to report product usage for resource in a
consumer project.

Hostname: resourceaccounting.cbws.xyz

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ListResources | [ListResourcesRequest](#cbws.service_management.resource_accounting.v1alpha1.ListResourcesRequest) | [ListResourcesResponse](#cbws.service_management.resource_accounting.v1alpha1.ListResourcesResponse) | Permission required: resourceaccounting.cbws.xyz/Resource/list |
| Account | [AccountRequest](#cbws.service_management.resource_accounting.v1alpha1.AccountRequest) | [AccountResponse](#cbws.service_management.resource_accounting.v1alpha1.AccountResponse) | Account usage for a resource in a consumer project

Permission required: servicemanagement.cbws.xyz/Service/accountUsage |

 



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

