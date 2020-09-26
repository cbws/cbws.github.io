# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [cbws/domains/v1alpha1/domain.proto](#cbws/domains/v1alpha1/domain.proto)
    - [Domain](#cbws.domains.v1alpha1.Domain)
  
- [cbws/domains/v1alpha1/domains.proto](#cbws/domains/v1alpha1/domains.proto)
    - [GetDomainRequest](#cbws.domains.v1alpha1.GetDomainRequest)
    - [ListDomainsRequest](#cbws.domains.v1alpha1.ListDomainsRequest)
    - [ListDomainsResponse](#cbws.domains.v1alpha1.ListDomainsResponse)
  
    - [DomainsService](#cbws.domains.v1alpha1.DomainsService)
  
- [Scalar Value Types](#scalar-value-types)



<a name="cbws/domains/v1alpha1/domain.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/domains/v1alpha1/domain.proto



<a name="cbws.domains.v1alpha1.Domain"></a>

### Domain



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | The resource name of the domain in the following format: `domains/{domain}`

We have chosen to not include the project prefix as domain names are globally unique. |
| parent | [string](#string) |  |  |
| unique_id | [string](#string) |  | @OutputOnly The unique and stable id of the service account. |
| domain | [string](#string) |  | The domain name part of the domain, in case of sidn.nl this would be sidn |
| tld | [string](#string) |  | The tld portion of the domain, for example nl, com, co.uk |
| expiry | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  | When the domain will expire |
| auto_renew | [bool](#bool) |  | Whether auto renew has been enabled for this domain |





 

 

 

 



<a name="cbws/domains/v1alpha1/domains.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## cbws/domains/v1alpha1/domains.proto



<a name="cbws.domains.v1alpha1.GetDomainRequest"></a>

### GetDomainRequest
The domain get request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Required. The resource name of the domain in the following format: `domains/{domain}`. |






<a name="cbws.domains.v1alpha1.ListDomainsRequest"></a>

### ListDomainsRequest
The domain list request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parent | [string](#string) |  | Required. The resource name of the project associated with the service accounts, such as `projects/my-project-123`. |
| page_size | [int32](#int32) |  | Optional limit on the number of domains to include in the response. Further accounts can subsequently be obtained by including the [ListDomainsResponse.next_page_token][cbws.domains.v1alpha1.ListDomainsResponse.next_page_token] in a subsequent request. |
| page_token | [string](#string) |  | Optional pagination token returned in an earlier [ListDomainsResponse.next_page_token][cbws.domains.v1alpha1.ListDomainsResponse.next_page_token]. |






<a name="cbws.domains.v1alpha1.ListDomainsResponse"></a>

### ListDomainsResponse
The domain list response.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| domains | [Domain](#cbws.domains.v1alpha1.Domain) | repeated | The list of matching domains. |
| next_page_token | [string](#string) |  | To retrieve the next page of results, set [ListDomainsRequest.page_token][cbws.domains.v1alpha1.ListDomainsRequest.page_token] to this value. |





 

 

 


<a name="cbws.domains.v1alpha1.DomainsService"></a>

### DomainsService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| ListDomains | [ListDomainsRequest](#cbws.domains.v1alpha1.ListDomainsRequest) | [ListDomainsResponse](#cbws.domains.v1alpha1.ListDomainsResponse) |  |
| GetDomain | [GetDomainRequest](#cbws.domains.v1alpha1.GetDomainRequest) | [Domain](#cbws.domains.v1alpha1.Domain) |  |

 



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

