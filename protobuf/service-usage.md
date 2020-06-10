# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/service_management/service_usage/v1alpha1/service.proto](#cbws/service_management/service_usage/v1alpha1/service.proto)
    - [Service](#cbws.service_management.service_usage.v1alpha1.Service)
    - [ServiceConfig](#cbws.service_management.service_usage.v1alpha1.ServiceConfig)
  
    - [ServiceState](#cbws.service_management.service_usage.v1alpha1.ServiceState)
  
- [cbws/service_management/service_usage/v1alpha1/service_management.proto](#cbws/service_management/service_usage/v1alpha1/service_management.proto)
    - [DisableServiceMetadata](#cbws.service_management.service_usage.v1alpha1.DisableServiceMetadata)
    - [DisableServiceRequest](#cbws.service_management.service_usage.v1alpha1.DisableServiceRequest)
    - [DisableServiceResponse](#cbws.service_management.service_usage.v1alpha1.DisableServiceResponse)
    - [EnableServiceMetadata](#cbws.service_management.service_usage.v1alpha1.EnableServiceMetadata)
    - [EnableServiceRequest](#cbws.service_management.service_usage.v1alpha1.EnableServiceRequest)
    - [EnableServiceResponse](#cbws.service_management.service_usage.v1alpha1.EnableServiceResponse)
    - [ListServicesRequest](#cbws.service_management.service_usage.v1alpha1.ListServicesRequest)
    - [ListServicesResponse](#cbws.service_management.service_usage.v1alpha1.ListServicesResponse)
  
    - [ServiceUsageService](#cbws.service_management.service_usage.v1alpha1.ServiceUsageService)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/service_management/service_usage/v1alpha1/service.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/service_management/service_usage/v1alpha1/service.proto



<a name="cbws.service_management.service_usage.v1alpha1.Service"></a>

### Service



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Service relative resource name, in the format of projects/test-project/services/k8s.cbws.xyz |
| parent | [string](#string) |  | Relative resource name of the parent resource, for example projects/test-project |
| config | [ServiceConfig](#cbws.service_management.service_usage.v1alpha1.ServiceConfig) |  | Overall information about the service, including service name (k8s.cbws.xyz) and title |
| state | [ServiceState](#cbws.service_management.service_usage.v1alpha1.ServiceState) |  | Whether the service is enabled on this project or not |






<a name="cbws.service_management.service_usage.v1alpha1.ServiceConfig"></a>

### ServiceConfig



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The name of the service, for example k8s.cbws.xyz |
| title | [string](#string) |  | The title of the product of the service, for example Kubernetes |





 


<a name="cbws.service_management.service_usage.v1alpha1.ServiceState"></a>

### ServiceState


| Name | Number | Description |
| ---- | ------ | ----------- |
| SERVICE_STATE_UNSPECIFIED | 0 |  |
| SERVICE_STATE_DISABLED | 1 | Service is currently not enabled in the consumer project |
| SERVICE_STATE_ENABLED | 2 | Service is enabled in the consumer project and can be used |


 

 

 



<a name="cbws/service_management/service_usage/v1alpha1/service_management.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/service_management/service_usage/v1alpha1/service_management.proto



<a name="cbws.service_management.service_usage.v1alpha1.DisableServiceMetadata"></a>

### DisableServiceMetadata







<a name="cbws.service_management.service_usage.v1alpha1.DisableServiceRequest"></a>

### DisableServiceRequest
Request message for DisableService method.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Relative resource of service in project in format: projects/test-project/services/iam.cbws.xyz |






<a name="cbws.service_management.service_usage.v1alpha1.DisableServiceResponse"></a>

### DisableServiceResponse
Operation payload for DisableService method.






<a name="cbws.service_management.service_usage.v1alpha1.EnableServiceMetadata"></a>

### EnableServiceMetadata







<a name="cbws.service_management.service_usage.v1alpha1.EnableServiceRequest"></a>

### EnableServiceRequest
Request message for EnableService method.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Relative resource of service in project in format: projects/test-project/services/iam.cbws.xyz |






<a name="cbws.service_management.service_usage.v1alpha1.EnableServiceResponse"></a>

### EnableServiceResponse
Operation payload for EnableService method.






<a name="cbws.service_management.service_usage.v1alpha1.ListServicesRequest"></a>

### ListServicesRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  |  |






<a name="cbws.service_management.service_usage.v1alpha1.ListServicesResponse"></a>

### ListServicesResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| services | [Service](#cbws.service_management.service_usage.v1alpha1.Service) | repeated | The list of matching services. |





 

 

 


<a name="cbws.service_management.service_usage.v1alpha1.ServiceUsageService"></a>

### ServiceUsageService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ListServices | [ListServicesRequest](#cbws.service_management.service_usage.v1alpha1.ListServicesRequest) | [ListServicesResponse](#cbws.service_management.service_usage.v1alpha1.ListServicesResponse) | Enables a service for a project, so it can be used for the project.

Operation&lt;response: EnableServiceResponse&gt; |
| EnableService | [EnableServiceRequest](#cbws.service_management.service_usage.v1alpha1.EnableServiceRequest) | [.google.longrunning.Operation](#google.longrunning.Operation) | Enables a service for a project, so it can be used for the project.

Operation&lt;response: EnableServiceResponse&gt; |
| DisableService | [DisableServiceRequest](#cbws.service_management.service_usage.v1alpha1.DisableServiceRequest) | [.google.longrunning.Operation](#google.longrunning.Operation) | Disables a service for a project, so it can no longer be be used for the project. It prevents accidental usage that may cause unexpected billing charges or security leaks.

Operation&lt;response: DisableServiceResponse&gt; |

 



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

