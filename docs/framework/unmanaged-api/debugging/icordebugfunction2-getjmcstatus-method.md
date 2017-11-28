---
title: "ICorDebugFunction2::GetJMCStatus 메서드"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dc5e5e6a0ff0784825a69ba1873224a537ad46c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="59e81-102">ICorDebugFunction2::GetJMCStatus 메서드</span><span class="sxs-lookup"><span data-stu-id="59e81-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="59e81-103">이 ICorDebugFunction2 개체로 표시 하는 함수는 사용자 코드로 표시 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="59e81-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e81-104">구문</span><span class="sxs-lookup"><span data-stu-id="59e81-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59e81-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="59e81-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="59e81-106">[out] 부울 값이에 대 한 포인터 `true`경우이 함수는 사용자 코드로 표시 됩니다. 그렇지 않으면 값은 `false`합니다.</span><span class="sxs-lookup"><span data-stu-id="59e81-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59e81-107">설명</span><span class="sxs-lookup"><span data-stu-id="59e81-107">Remarks</span></span>  
 <span data-ttu-id="59e81-108">이 나타내는 함수 `ICorDebugFunction2` 디버깅할 수 없습니다 `pbIsJustMyCode` 항상 `false`합니다.</span><span class="sxs-lookup"><span data-stu-id="59e81-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59e81-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="59e81-109">Requirements</span></span>  
 <span data-ttu-id="59e81-110">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="59e81-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59e81-111">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59e81-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59e81-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59e81-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59e81-113">**.NET framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59e81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>