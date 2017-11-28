---
title: "IAssemblyCache 인터페이스"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="60edd-102">IAssemblyCache 인터페이스</span><span class="sxs-lookup"><span data-stu-id="60edd-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="60edd-103">Fusion 기술에서 사용 하기 위해 전역 어셈블리 캐시를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60edd-104">메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-104">Methods</span></span>  
  
|<span data-ttu-id="60edd-105">메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-105">Method</span></span>|<span data-ttu-id="60edd-106">설명</span><span class="sxs-lookup"><span data-stu-id="60edd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60edd-107">CreateAssemblyCacheItem 메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="60edd-108">새에 대 한 참조 [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="60edd-109">CreateAssemblyScavenger 메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="60edd-110">Fusion 기술에서 내부 사용을 위해 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="60edd-111">InstallAssembly 메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="60edd-112">전역 어셈블리 캐시에 지정된 된 어셈블리를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="60edd-113">QueryAssemblyInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="60edd-114">지정된 된 어셈블리에 대 한 요청 된 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="60edd-115">UninstallAssembly 메서드</span><span class="sxs-lookup"><span data-stu-id="60edd-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="60edd-116">지정된 된 어셈블리를 전역 어셈블리 캐시에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60edd-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="60edd-117">Requirements</span></span>  
 <span data-ttu-id="60edd-118">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="60edd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60edd-119">**헤더:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="60edd-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="60edd-120">**.NET framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60edd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60edd-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60edd-121">See Also</span></span>  
 [<span data-ttu-id="60edd-122">Fusion 인터페이스</span><span class="sxs-lookup"><span data-stu-id="60edd-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="60edd-123">전역 어셈블리 캐시</span><span class="sxs-lookup"><span data-stu-id="60edd-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)