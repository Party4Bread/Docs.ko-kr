---
title: '방법: 전역 프록시 선택 재정의'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 244315b5df4200524685bc5b9fb75a0d7fd9b39e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44185037"
---
# <a name="how-to-override-a-global-proxy-selection"></a>방법: 전역 프록시 선택 재정의
이 예제에서는 글로벌 프록시 선택을 포트 80의 `alternateproxy`라는 프록시 서버로 재정의하는 **WebRequest**를 `www.contoso.com`에 보냅니다.  
  
## <a name="example"></a>예  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 이 예제에는 다음 사항이 필요합니다.  
  
-   **System.Net** 네임스페이스에 대한 [`using` 지시문](~/docs/csharp/language-reference/keywords/using-directive.md)  
  
## <a name="see-also"></a>참고 항목  
 [응용 프로그램 프로토콜 사용](../../../docs/framework/network-programming/using-application-protocols.md)  
 [프록시를 통해 인터넷 액세스](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
