---
title: WCF 웹 HTTP 서비스에 대한 캐싱 지원
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 25b564235b5d2b3b26b5d657f3e5f0bd5d594125
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185076"
---
# <a name="caching-support-for-wcf-web-http-services"></a>WCF 웹 HTTP 서비스에 대한 캐싱 지원
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] WCF 웹 HTTP 서비스에서 ASP.NET에 이미 사용 가능한 선언적 캐싱 메커니즘을 사용할 수 있습니다. 이렇게 하면 WCF 웹 HTTP 서비스 작업의 응답을 캐시할 수 있습니다. 사용자가 캐시용으로 구성된 서비스에 HTTP GET을 보내면 ASP.NET이 캐시된 응답을 다시 보내고 서비스 메서드가 호출되지 않습니다. 캐시가 만료되면 다음에 사용자가 HTTP GET을 보낼 때 서비스 메서드가 호출되고 응답이 다시 한 번 캐시됩니다. ASP.NET 캐싱에 대 한 자세한 내용은 참조 하세요. [ASP.NET 캐싱 개요](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>기본 웹 HTTP 서비스 캐싱  
 웹 HTTP 서비스 캐싱을 사용하도록 설정하려면 먼저 서비스에 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>를 적용하여 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A>를 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> 또는 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>로 설정하여 ASP.NET 호환성을 사용하도록 설정해야 합니다.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]에서는 캐시 프로필 이름을 지정할 수 있는 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>라는 새로운 특성을 제공합니다. 이 특성은 서비스 작업에 적용됩니다. 다음 예제에서는 서비스에 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>를 적용하여 ASP.NET 호환성을 사용하도록 설정하고 `GetCustomer` 작업을 캐시용으로 구성합니다. 합니다 <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` 특성에 사용할 캐시 설정이 포함 된 캐시 프로필을 지정 합니다.  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 다음 예제와 같이 Web.config 파일에서도 ASP.NET 호환성 모드를 사용하도록 설정해야 합니다.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  ASP.NET 호환성 모드가 사용되도록 설정되어 있지 않은 경우 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>를 사용하면 예외가 throw됩니다.  
  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>에 지정된 캐시 프로필 이름은 Web.config 구성 파일에 추가되는 캐시 프로필을 식별합니다. 캐시 프로필에 사용 하 여 정의 된를 <`outputCacheSetting`> 다음 구성 예제와 같이 요소입니다.  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 이 요소는 ASP.NET 응용 프로그램에서 사용할 수 있는 구성 요소와 동일합니다. ASP.NET 캐시 프로필에 대 한 자세한 내용은 참조 하세요. <xref:System.Web.Configuration.OutputCacheProfile>합니다. 웹 HTTP 서비스의 경우 캐시 프로필에서 가장 중요한 특성이 `cacheDuration` 및 `varyByParam`입니다. 두 특성 모두 필요합니다. `cacheDuration`은 응답이 캐시되어야 하는 기간(초)을 설정합니다. `varyByParam`에서는 응답을 캐시하는 데 사용하는 쿼리 문자열 매개 변수를 지정할 수 있습니다. 여러 쿼리 문자열 매개 변수 값을 사용하여 수행한 모든 요청은 개별적으로 캐시됩니다. 예를 들어 초기 요청에 설정 되 면 http://MyServer/MyHttpService/MyOperation?param=10 동일한 URI를 사용 하 여 만든 모든 후속 요청 반환 됩니다 캐시 된 응답 (된다면 캐시 기간 경과 하지 않습니다). 동일하지만 쿼리 문자열 매개 변수 값이 다른 유사한 요청에 대한 응답은 개별적으로 캐시됩니다. 이 개별 캐시 동작을 사용하지 않으려면 `varyByParam`을 "none"으로 설정합니다.  
  
## <a name="sql-cache-dependency"></a>SQL 캐시 종속성  
 웹 HTTP 서비스 응답도 SQL 캐시 종속성을 사용하여 캐시할 수 있습니다. WCF 웹 HTTP 서비스에서 SQL 데이터베이스에 저장된 데이터를 사용하는 경우 이 서비스의 응답을 캐시하고 SQL 데이터베이스 테이블의 데이터가 변경되면 캐시된 응답을 무효화할 수 있습니다. 이 동작은 Web.config 파일에서 완전히 구성할 수 있습니다. 연결 문자열을 정의 해야 합니다 <`connectionStrings`> 요소입니다.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 다음 안에서 SQL 캐시 종속성을 사용 하도록 설정 해야 합니다는 <`caching`> 내의 요소는 <`system.web`> 다음 구성 예제에서와 같이 요소입니다.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 여기서 SQL 캐시 종속성이 사용되도록 설정되었고 폴링 시간이 1000밀리초로 설정되었습니다. 폴링 시간이 만료될 때마다 데이터베이스 테이블이 업데이트되었는지 확인하는 작업이 수행됩니다. 변경 내용이 감지되면 캐시의 내용이 제거되고 다음에 서비스 작업이 호출될 때 새 응답이 캐시됩니다. 내는 <`sqlCacheDependency`> 요소는 데이터베이스를 추가 하 고 내에서 연결 문자열을 참조 합니다 <`databases`> 다음 예제에서와 같이 요소입니다.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 안에서 출력 캐시 설정을 구성 해야 하는 다음의 <`caching`> 요소는 다음 예와에서 같이 합니다.  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 여기서 캐시 기간이 60초로 설정되었고, `varyByParam`이 none으로 설정되었으며, `sqlDependency`가 콜론으로 구분된 데이터베이스/테이블 쌍의 세미콜론으로 구분된 목록으로 설정되었습니다. `MyTable`의 데이터가 변경되면 서비스 작업의 캐시된 응답이 제거되고, 서비스 작업이 호출되면 새 응답이 생성 및 캐시된 후 클라이언트에 반환됩니다.  
  
> [!IMPORTANT]
>  SQL 데이터베이스에 액세스 하려면 asp.net을 사용 해야 합니다 [ASP.NET SQL Server 등록 도구](https://go.microsoft.com/fwlink/?LinkId=152536)합니다. 또한 적절한 사용자 계정을 사용하여 데이터베이스와 테이블에 액세스할 수 있도록 해야 합니다. 자세한 내용은 [웹 응용 프로그램에서 SQL Server 액세스](https://go.microsoft.com/fwlink/?LinkId=178988)합니다.  
  
## <a name="conditional-http-get-based-caching"></a>조건부 HTTP GET 기반 캐싱  
 웹 HTTP 시나리오에서 조건부 HTTP GET은 서비스에서 자주 사용에 설명 된 대로 지능형 HTTP 캐싱을 구현 하는 [HTTP 사양](https://go.microsoft.com/fwlink/?LinkId=165800)합니다. 서비스에서 지능형 HTTP 캐싱을 구현하려면 HTTP 응답에 있는 ETag 헤더의 값을 설정하고 HTTP 요청에 있는 If-None-Match 헤더를 검사하여 지정된 ETag가 현재 ETag와 일치하는지 여부도 확인해야 합니다.  
  
 GET 및 HEAD 요청의 경우 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>는 ETag 값을 가져와서 요청의 If-None-Match 헤더와 비교합니다. 이 헤더가 있고 ETag 값과 일치하면 HTTP 상태 코드 304(수정 안 됨)와 함께 <xref:System.ServiceModel.Web.WebFaultException>이 throw되고 일치하는 ETag가 있는 응답에 ETag 헤더가 추가됩니다.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 메서드의 한 오버로드는 마지막으로 수정한 날짜를 가져와서 요청의 If-Modified-Since 헤더와 비교합니다. 이 헤더가 있고 리소스가 수정되지 않은 경우 HTTP 상태 코드 304(수정 안 됨)와 함께 <xref:System.ServiceModel.Web.WebFaultException>이 throw됩니다.  
  
 PUT, POST 및 DELETE 요청의 경우 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A>는 리소스의 현재 ETag 값을 사용합니다. 메서드-None-If-match 헤더의 값을 갖도록 확인 현재 ETag 값이 null 이면 "*"입니다.  현재 ETag 값이 기본값이 아니면 이 메서드는 현재 ETag 값을 요청의 If- Match 헤더와 비교합니다. 두 경우 모두 예상 헤더가 요청에 없거나 해당 값이 조건부 검사를 충족하지 못하면 이 메서드는 HTTP 상태 코드 412(사전 조건 실패)와 함께 <xref:System.ServiceModel.Web.WebFaultException>을 throw하고 응답의 ETag 헤더를 현재 ETag 값으로 설정합니다.  
  
 `CheckConditional` 메서드와 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> 메서드는 모두 HTTP 사양에 따라 응답 헤더에 설정된 ETag 값이 유효한 ETag인지 확인합니다. 여기에는 이러한 ETag 값이 아직 없고 내부 큰따옴표 문자로 올바로 이스케이프되지 않는 경우 큰따옴표로 이러한 값을 묶는 작업이 포함됩니다. 약한 ETag 비교는 지원되지 않습니다.  
  
 다음 예제에서는 이러한 메서드를 사용하는 방법을 보여 줍니다.  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a>보안 고려 사항  
 응답이 캐시에서 제공될 때는 권한 부여가 수행되지 않으므로 권한 부여가 필요한 요청의 경우 응답이 캐시되지 않아야 합니다.  이러한 응답을 캐시하면 보안이 심각하게 취약해집니다.  일반적으로 권한 부여가 필요한 요청에서는 사용자별 데이터를 제공하므로 서버 쪽 캐싱도 효과적이지 않습니다.  이러한 경우 클라이언트 쪽 캐싱을 사용하거나 캐싱을 전혀 사용하지 않는 것이 더 적절합니다.
