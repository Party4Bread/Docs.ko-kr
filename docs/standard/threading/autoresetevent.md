---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7602a61a4403b7ab85015876823aa41e250b23de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863311"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> 클래스는 단일 대기 스레드를 해제한 후 신호를 받을 때 자동으로 다시 설정되는 로컬 대기 핸들 이벤트를 나타냅니다. 이 클래스는 기본 클래스인 <xref:System.Threading.EventWaitHandle>의 특수한 경우를 나타냅니다. 자동 재설정 이벤트의 사용 및 기능은 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 개념 설명서를 참조하세요.  
  
 단일 대기 스레드가 해제된 후 <xref:System.Threading.AutoResetEvent> 개체가 시스템의 신호를 받지 않음으로 자동으로 다시 설정됩니다. 대기 스레드가 없으면 이벤트 개체의 상태는 신호를 받은 것으로 유지됩니다. <xref:System.Threading.AutoResetEvent>는 `bManualReset` 인수에 대해 `false`를 지정하는 Win32 `CreateEvent` 호출에 해당합니다.  
  
 <xref:System.Threading.AutoResetEvent>를 사용하는 예제는 <xref:System.Threading.Monitor>를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [스레딩](../../../docs/standard/threading/index.md)  
- [스레딩 개체 및 기능](../../../docs/standard/threading/threading-objects-and-features.md)  
- [대기 핸들](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
