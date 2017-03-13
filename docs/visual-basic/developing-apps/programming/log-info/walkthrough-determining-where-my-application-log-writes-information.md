---
title: "연습: My.Application.Log가 정보를 기록하는 위치 확인(Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Log 개체, 출력 위치"
  - "출력, 응용 프로그램 로그 위치"
  - "My.Application.Log 개체, 출력 위치"
  - "이벤트 로그, 출력 위치 확인"
  - "응용 프로그램 이벤트 로그, 출력 위치"
  - "응용 프로그램[Visual Basic], 출력 위치"
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# 연습: My.Application.Log가 정보를 기록하는 위치 확인(Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Application.Log` 개체는 여러 로그 수신기에 정보를 쓸 수 있습니다. 로그 수신기는 컴퓨터의 구성 파일로 구성되며 응용 프로그램의 구성 파일로 재정의할 수 있습니다. 이 항목에서는 기본 설정과 응용 프로그램의 설정을 확인하는 방법을 설명합니다.  
  
 기본 출력 위치에 대한 자세한 내용은 [응용 프로그램 로그 작업](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)을 참조하세요.  
  
### My.Application.Log의 수신기를 확인하려면  
  
1.  어셈블리의 구성 파일을 찾습니다. 어셈블리를 개발하는 경우 **솔루션 탐색기**에서 [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)]의 app.config에 액세스할 수 있습니다. 그렇지 않은 경우 구성 파일 이름은 어셈블리의 이름에 ".config"가 붙은 형태이며 어셈블리와 같은 디렉터리에 위치합니다.  
  
    > [!NOTE]
    >  구성 파일에 없는 어셈블리도 있습니다.  
  
     구성 파일은 XML 파일입니다.  
  
2.  `name` 특성이 "DefaultSource"인 `<source>` 섹션에서 `<sources>` 섹션에 있는 `<listeners>` 섹션을 찾습니다.`<sources>` 섹션은 최상위 `<configuration>` 섹션의 `<system.diagnostics>` 섹션에 있습니다.  
  
     이들 섹션이 없으면 컴퓨터의 구성 파일이 `My.Application.Log` 로그 수신기를 구성합니다. 다음 단계에서는 컴퓨터 구성 파일에 정의된 내용을 확인하는 방법을 설명합니다.  
  
    1.  컴퓨터의 machine.config 파일을 찾습니다. 이 파일은 일반적으로 *SystemRoot\\Microsoft.NET\\Framework\\frameworkVersion\\CONFIG* 디렉터리에 있으며, 여기서 `SystemRoot`는 운영 체제 디렉터리이고 `frameworkVersion`은 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)]의 버전입니다.  
  
         machine.config의 설정은 응용 프로그램의 구성 파일로 재정의할 수 있습니다.  
  
         아래 나열된 선택적 요소가 없을 경우 새로 만들 수 있습니다.  
  
    2.  최상위 `<configuration>` 섹션의 `<system.diagnostics>` 섹션에 있는 `<sources>` 섹션에서 `name` 특성이 "DefaultSource"인 `<source>` 섹션에 있는 `<listeners>` 섹션을 찾습니다.  
  
         이들 섹션이 없으면 `My.Application.Log`에 기본 로그 수신기만 있는 경우입니다.  
  
3.  \<`listeners>` 섹션에서 \<`add>` 요소를 찾습니다.  
  
     이들 요소는 명명된 로그 수신기를 `My.Application.Log` 소스에 추가합니다.  
  
4.  최상위 `<configuration>` 섹션에 있는 `<system.diagnostics>` 섹션의 `<sharedListeners>` 섹션에서 로그 수신기의 이름이 지정된 `<add>` 요소를 찾습니다.  
  
5.  여러 형식의 공유 수신기의 경우, 수신기의 초기화 데이터에는 수신기가 데이터를 보낼 위치에 대한 설명이 포함되어 있습니다.  
  
    -   소개에서 설명한 것처럼 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> 수신기는 파일 로그에 씁니다.  
  
    -   <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> 수신기는 `initializeData` 매개 변수로 지정된 컴퓨터 이벤트 로그에 정보를 씁니다. 이벤트 로그를 보려면 **서버 탐색기** 또는 **Windows 이벤트 뷰어**를 사용합니다. 자세한 내용은 [.NET Framework의 ETW 이벤트](../Topic/ETW%20Events%20in%20the%20.NET%20Framework.md)을 참조하세요.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> 및 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> 수신기는 `initializeData` 매개 변수에 지정된 파일에 씁니다.  
  
    -   <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> 수신기는 명령줄 콘솔에 씁니다.  
  
    -   다른 형식의 로그 수신기가 정보를 쓰는 위치에 대한 자세한 내용은 해당 형식의 설명서를 참조하세요.  
  
## 참고 항목  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:System.Diagnostics.DefaultTraceListener>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 <xref:System.Diagnostics.DelimitedListTraceListener>   
 <xref:System.Diagnostics.XmlWriterTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics>   
 [응용 프로그램 로그 작업](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [방법: 로그 메시지 쓰기](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [연습: My.Application.Log가 정보를 기록하는 위치 변경](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)   
 [.NET Framework의 ETW 이벤트](../Topic/ETW%20Events%20in%20the%20.NET%20Framework.md)   
 [Troubleshooting: Log Listeners](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)