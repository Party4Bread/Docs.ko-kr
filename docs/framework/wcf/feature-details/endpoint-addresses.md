---
title: "끝점 주소 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "주소 [WCF]"
  - "WCF [WCF], 주소"
  - "Windows Communication Foundation [WCF], 주소"
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 끝점 주소
모든 끝점에는 해당 끝점을 찾아서 식별하는 데 사용되는 연결된 주소가 있습니다.이 주소는 주로 끝점의 위치를 지정하는 URI\(Uniform Resource Identifier\)로 구성됩니다.끝점 주소는 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 프로그래밍 모델에 <xref:System.ServiceModel.EndpointAddress> 클래스로 표시됩니다. 이 클래스에는 한 끝점에서 다른 끝점과 메시지를 교환할 때 상대 끝점을 인증할 수 있도록 하는 선택적 <xref:System.ServiceModel.EndpointAddress.Identity%2A> 속성과 서비스에 연결하는 데 필요한 다른 SOAP 헤더를 정의하는 선택적 <xref:System.ServiceModel.EndpointAddress.Headers%2A> 속성 집합이 포함되어 있습니다.선택적 헤더는 서비스 끝점을 확인하거나 상호 작용하는 데 필요한 추가적인 자세한 주소 지정 정보를 제공합니다.끝점 주소는 통신 중에 WS\-Addressing EPR\(끝점 참조\)로 표시됩니다.  
  
## 주소의 URI 구조  
 대부분 전송 주소 URI에는 네 가지 부분이 있습니다.예를 들어 URI http:\/\/www.fabrikam.com:322\/mathservice.svc\/secureEndpoint의 네 부분을 다음과 같이 항목화할 수 있습니다.  
  
-   스키마: http:  
  
-   시스템: www.fabrikam.com  
  
-   \(선택적\) 포트: 322  
  
-   경로: \/mathservice.svc\/secureEndpoint  
  
## 서비스에 대한 주소 정의  
 서비스의 끝점 주소는 코드를 사용하여 명령적으로 지정하거나 구성을 통해 선언적으로 지정할 수 있습니다.일반적으로 배포된 서비스의 바인딩 및 주소는 서비스 개발 중에 사용된 바인딩 및 주소와 다르기 때문에 코드로 끝점을 정의하는 것은 효과적이지 않습니다.일반적으로 코드 대신 구성을 사용하여 서비스 끝점을 정의하는 것이 좋습니다.바인딩 및 주소 지정 정보를 코드와 구분하면 응용 프로그램을 다시 컴파일하거나 재배포할 필요 없이 해당 정보를 변경할 수 있습니다.  
  
### 구성에서 주소 정의  
 구성 파일에 끝점을 정의하려면 [\<endpoint\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) 요소를 사용합니다.자세한 내용 및 예제를 보려면 [끝점 주소 지정](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)을 참조하십시오.  
  
### 코드에서 주소 정의  
 끝점 주소는 <xref:System.ServiceModel.EndpointAddress> 클래스를 사용하여 코드에 만들 수 있습니다.자세한 내용 및 예제를 보려면 [끝점 주소 지정](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)을 참조하십시오.  
  
### WSDL의 끝점  
 끝점 주소는 해당 끝점의 `wsdl:port` 요소 내에 있는 WS\-Addressing EPR 요소로 WSDL에서 나타낼 수도 있습니다.EPR에는 끝점 주소와 주소 속성이 포함되어 있습니다.자세한 내용 및 예제를 보려면 [끝점 주소 지정](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)을 참조하십시오.  
  
## .NET Framework 3.5의 여러 IIS 바인딩 지원  
 인터넷 서비스 공급자는 사이트 밀도를 높이고 총 소유 비용을 줄이기 위해 종종 같은 서버 및 사이트에서 여러 응용 프로그램을 호스팅합니다.이러한 응용 프로그램은 일반적으로 다른 기본 주소로 바인딩됩니다.IIS\(인터넷 정보 서비스\) 웹 사이트에 여러 개의 응용 프로그램이 포함될 수 있습니다.하나 이상의 IIS 바인딩을 통해 한 사이트의 응용 프로그램에 액세스할 수 있습니다.  
  
 IIS 바인딩은 바인딩 프로토콜과 바인딩 정보라는 두 가지 정보를 제공합니다.바인딩 프로토콜은 통신이 이루어지는 스키마를 정의하며, 바인딩 정보는 사이트에 액세스하는 데 사용되는 정보입니다.  
  
 다음 예제에서는 IIS 바인딩에 나타낼 수 있는 구성 요소를 보여 줍니다.  
  
-   바인딩 프로토콜: HTTP  
  
-   바인딩 정보: IP 주소, 포트, 호스트 헤더  
  
 IIS에서는 각 사이트에 대해 여러 개의 바인딩을 지정할 수 있으므로, 각 스키마에 대해 여러 개의 기본 주소가 생성됩니다.[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 이전에 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]는 한 개의 스키마에 대해 여러 개의 주소를 지원하지 않았으며, 여러 개의 주소가 지정된 경우 활성화 중에 <xref:System.ArgumentException>을 throw했습니다.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]를 사용하면 인터넷 서비스 공급자가 동일한 사이트의 동일한 스키마에 대해 기본 주소가 다른 여러 응용 프로그램을 호스팅할 수 있습니다.  
  
 예를 들어 사이트에 다음 기본 주소가 포함될 수 있습니다.  
  
-   http:\/\/payroll.myorg.com\/Service.svc  
  
-   http:\/\/shipping.myorg.com\/Service.svc  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]를 사용하여 구성 파일의 AppDomain 수준에서 접두사 필터를 지정합니다.접두사 목록이 포함된 [\<baseAddressPrefixFilters\>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) 요소를 사용하여 이 작업을 수행합니다.IIS에서 제공하는 들어오는 기본 주소는 선택적 접두사 목록을 기반으로 필터링됩니다.기본적으로 접두사가 지정되지 않으면 모든 주소가 통과됩니다.접두사를 지정하면 해당 스키마에서 일치하는 기본 주소만 통과됩니다.  
  
 다음은 접두사 필터를 사용하는 구성 코드의 예제입니다.  
  
```  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 앞의 예제에서 net.tcp:\/\/payroll.myorg.com:8000 및 http:\/\/shipping.myorg.com:8000은 해당 스키마에 대해 통과되는 유일한 기본 주소입니다.  
  
 `baseAddressPrefixFilter`는 와일드카드를 지원하지 않습니다.  
  
 IIS에서 제공하는 기본 주소에 `baseAddressPrefixFilters` 목록에 없는 다른 체계에 바인딩되는 주소가 포함될 수 있습니다.이러한 주소는 필터링되지 않습니다.  
  
## .NET Framework 4 이상 버전에서 여러 IIS 바인딩 지원  
 .NET 4부터는 단일 기본 주소를 선택해야 할 필요 없이 <xref:System.ServiceModel.ServiceHostingEnvironment>의 <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 설정을 true로 설정하여 IIS에서 여러 바인딩을 지원할 수 있습니다.이 지원은 HTTP 프로토콜 체계로 제한됩니다.  
  
 다음은 [\<serviceHostingEnvironment\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)에서 multipleSiteBindingsEnabled를 사용하는 구성 코드의 예제입니다.  
  
```  
  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled=”true” >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 이 설정을 사용하여 여러 사이트 바인딩을 사용하도록 설정하는 경우 HTTP 프로토콜과 그 외의 프로토콜에 대한 모든 baseAddressPrefixFilters 설정이 무시됩니다.  
  
 자세한 내용과 예제를 보려면 [여러 IIS 사이트 바인딩 지원](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) 및 <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>를 참조하십시오.  
  
## WCF 서비스에서 주소 확장  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 서비스의 기본 주소 지정 모델은 다음과 같은 용도로 끝점 주소 URI를 사용합니다.  
  
-   끝점이 메시지를 수신 대기하는 위치인 서비스 수신 대기 주소 지정  
  
-   끝점이 SOAP 헤더로 간주하는 주소인 SOAP 주소 필터 지정  
  
 이러한 각 목적에 대해 값을 별도로 지정할 수 있으며, 이렇게 하면 유용한 시나리오를 다루는 여러 가지 주소 지정 확장을 사용할 수 있습니다.  
  
-   SOAP 매개자: 클라이언트가 보낸 메시지는 메시지가 최종 대상에 도달하기 전에 메시지를 처리하는 하나 이상의 추가 서비스를 통과합니다.SOAP 매개자는 메시지에 캐싱, 라우팅, 부하 분산 또는 스키마 유효성 검사 등의 여러 가지 작업을 수행할 수 있습니다.이 시나리오는 최종 대상을 지정하는 논리적 주소\(`wsa:To`\)가 아니라 매개자를 대상으로 하는 메시지를 별도의 실제 주소\(`via`\)로 보내어 수행됩니다.  
  
-   끝점의 수신 대기 주소는 개인 URI이며 해당 `listenURI` 속성과 다른 값으로 설정됩니다.  
  
 `via`에서 지정하는 전송 주소는 `to` 매개 변수에서 지정하는 다른 원격 주소\(서비스가 있는 주소\)로 가기 위해 메시지가 처음 전송되어야 하는 위치입니다.대부분의 인터넷 시나리오에서 `via` URI는 서비스의 최종 `to` 주소의 <xref:System.ServiceModel.EndpointAddress.Uri%2A> 속성과 같습니다.수동 라우팅을 수행해야 하는 경우에만 이 두 주소를 구별합니다.  
  
### 주소 지정 헤더  
 하나 이상의 SOAP 헤더와 해당 기본 URI로 끝점에 주소를 지정할 수 있습니다.이 유용한 하나의 시나리오 집합이 SOAP 매개 시나리오 집합입니다. 이 시나리오 집합에서는 끝점에 매개자를 대상으로 한 SOAP 헤더를 포함할 해당 끝점의 클라이언트가 필요합니다.  
  
 코드나 구성을 사용하여 사용자 지정 주소 헤더를 정의할 수 있습니다.  
  
-   코드에서는 <xref:System.ServiceModel.Channels.AddressHeader> 클래스를 사용하여 사용자 지정 주소 헤더를 만든 다음 <xref:System.ServiceModel.EndpointAddress> 생성에 사용합니다.  
  
-   구성에서는 사용자 지정 [\<headers\>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)[\<endpoint\>가](http://msdn.microsoft.com/ko-kr/13aa23b7-2f08-4add-8dbf-a99f8127c017) 요소의 자식으로 지정됩니다.  
  
 일반적으로 구성을 사용하면 배포 후에 헤더를 변경할 수 있으므로 구성을 사용하는 것이 코드를 사용하는 것보다 낫습니다.  
  
### 사용자 지정 수신 대기 주소  
 수신 대기 주소를 끝점의 URI 이외의 다른 값으로 설정할 수 있습니다.이 기능은 노출할 SOAP 주소가 공용 SOAP 매개자의 주소이지만 실제로 수신 대기하는 끝점이 개인 네트워크 주소인 매개 시나리오에서 유용합니다.  
  
 코드나 구성을 사용하여 사용자 지정 수신 대기 주소를 지정할 수 있습니다.  
  
-   코드에서는 <xref:System.ServiceModel.Description.ClientViaBehavior> 클래스를 끝점의 동작 컬렉션에 추가하여 사용자 지정 수신 대기 주소를 지정합니다.  
  
-   구성에서는 서비스 [\<endpoint\>](http://msdn.microsoft.com/ko-kr/13aa23b7-2f08-4add-8dbf-a99f8127c017) 요소의 `ListenUri` 특성과 함께 사용자 지정 수신 대기 주소를 지정합니다.  
  
### 사용자 지정 SOAP 주소 필터  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A>는 <xref:System.ServiceModel.EndpointAddress.Headers%2A> 속성과 함께 사용되어 끝점의 SOAP 주소 필터\(<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>\)를 정의합니다.기본적으로 이 필터는 들어오는 메시지에 끝점의 URI와 일치하는 `To` 메시지 헤더가 있는지, 모든 필수 끝점 헤더가 메시지에 있는지 확인합니다.  
  
 일부 시나리오에서 끝점은 기본 전송에 도착하는 모든 메시지를 받고 해당 `To` 헤더가 있는 메시지는 받지 않습니다.이 기능을 사용하도록 설정하려면 사용자가 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 클래스를 사용합니다.  
  
## 참고 항목  
 [끝점 주소 지정](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)   
 [서비스 ID 및 인증](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)