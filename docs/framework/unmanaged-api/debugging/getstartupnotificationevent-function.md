---
title: GetStartupNotificationEvent 함수
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3692471e0652a1a812b1d0cbed9e38cc32112ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404312"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent 함수
지정된 대상 프로세스에 로드 중인 CLR(공용 언어 런타임)에서 신호를 전송할 이벤트 핸들을 만들거나 엽니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `debuggeePID`  
 [in] CLR 시작 알림을 수신할 대상 프로세스의 프로세스 식별자입니다.  
  
 `phStartupEvent`  
 [out] 시작 시 CLR에서 신호를 전송할 핸들에 대한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 S_OK  
 시작 알림 이벤트에 대한 핸들을 성공적으로 가져왔습니다.  
  
 E_INVALIDARG  
 `phStartupEvent`가 null이거나 `debuggeePID`가 현재 실행 중인 프로세스를 참조하지 않습니다.  
  
 E_FAIL(또는 다른 E_ 반환 코드)  
 시작 알림 이벤트에 대한 핸들을 가져올 수 없습니다.  
  
## <a name="remarks"></a>설명  
 Windows 운영 체제에서 `debuggeePID`는 OS 프로세스 식별자에 매핑됩니다.  
  
 이벤트 신호를 전송한 CLR에서 관리 코드를 실행하기 전에 이벤트 신호가 전송됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** dbgshim.h  
  
 **라이브러리:** dbgshim.dll  
  
 **.NET framework 버전:** 3.5 SP1
