---
title: 기본적인 XAML 전용 서비스
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: f4f296a97b9c3093874c5ec8e05023e84b0af44a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268801"
---
# <a name="basic-xaml-only-service"></a>기본적인 XAML 전용 서비스
이 샘플에서는 XAML로만 구성된 서비스를 만드는 방법을 보여 줍니다. 이 시나리오는 자동차 관련 문제에 대한 진단 서비스입니다. 이 서비스는 문제를 진단하기 위해 고객에게 일련의 질문을 하는 워크플로로 구현됩니다. 이 서비스로 진단할 수 있는 문제에는 두 가지 유형이 있습니다. 그 중 하나는 자동차의 시동이 걸리지 않는 문제이고, 다른 하나는 공조기가 작동하지 않는 문제입니다. 이 워크플로에서는 디자이너의 요청/회신 템플릿을 사용하여 간단한 서비스 작업 세 가지를 노출합니다. 서비스는 IIS에 가상 디렉터리를 만들고 service1.xamlx와 Web.config 파일을 가상 디렉터리에 복사하여 IIS에서 호스트되며 컴파일된 코드는 필요하지 않습니다. 기본적으로이 샘플은 자동으로 필요한 파일을 복사 합니다 WCF 및 WF 샘플에 대 한 설치 지침을 수행할 때 만든 가상 디렉터리: [the Windows Communication Foundation Samples일회설치절차](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010에서 작성 하는 경우.  
  
#### <a name="to-use-this-sample"></a>이 샘플을 사용하려면  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]에 프로젝트 솔루션을 로드하고 프로젝트를 빌드합니다.  
  
2.  [solution base directory]\Client\bin\debug에 생성된 클라이언트 응용 프로그램을 실행합니다.  
  
3.  응용 프로그램에 옵션이 출력되면 옵션을 선택합니다. 그런 다음 응용 프로그램에 몇 가지 질문이 표시되면 Y/N 키를 사용하여 예 또는 아니요로 답합니다. 서비스를 통해 문제 진단이 완료되면 진단 결과가 응용 프로그램에 출력됩니다.  
  
4.  응용 프로그램이 옵션 화면으로 되돌아갑니다. 여기에서 다른 문제를 진단하거나 응용 프로그램을 끝낼 수 있습니다.  
  
> [!IMPORTANT]
>  컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  이 디렉터리가 없으면로 이동 [Windows Communication Foundation (WCF) 및.NET Framework 4 용 Windows WF (Workflow Foundation) 샘플](https://go.microsoft.com/fwlink/?LinkId=150780) 모든 Windows Communication Foundation (WCF)를 다운로드 하 고 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 샘플. 이 샘플은 다음 디렉터리에 있습니다.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`