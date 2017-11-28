---
title: ICorDebugModuleEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleEnum
helpviewer_keywords: ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 106c052c41962d4881ed88a9a7fa69a506119bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenum-interface1"></a><span data-ttu-id="7bcad-102">ICorDebugModuleEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="7bcad-102">ICorDebugModuleEnum Interface1</span></span>
<span data-ttu-id="7bcad-103">ICorDebugEnum 메서드를 구현 하 고 ICorDebugModule 배열을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bcad-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bcad-104">메서드</span><span class="sxs-lookup"><span data-stu-id="7bcad-104">Methods</span></span>  
  
|<span data-ttu-id="7bcad-105">메서드</span><span class="sxs-lookup"><span data-stu-id="7bcad-105">Method</span></span>|<span data-ttu-id="7bcad-106">설명</span><span class="sxs-lookup"><span data-stu-id="7bcad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bcad-107">Next 메서드</span><span class="sxs-lookup"><span data-stu-id="7bcad-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="7bcad-108">지정된 된 수의 가져옵니다 `ICorDebugModule` 인스턴스 현재 위치부터 시작 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="7bcad-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bcad-109">설명</span><span class="sxs-lookup"><span data-stu-id="7bcad-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bcad-110">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7bcad-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bcad-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7bcad-111">Requirements</span></span>  
 <span data-ttu-id="7bcad-112">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7bcad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bcad-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bcad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bcad-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bcad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bcad-115">**.NET framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bcad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bcad-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7bcad-116">See Also</span></span>  
 [<span data-ttu-id="7bcad-117">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7bcad-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)