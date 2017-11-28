---
title: "파이프라인 개발"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4991fc65a48d620d30d09c44f1a30c2d1839071e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="pipeline-development"></a><span data-ttu-id="73849-102">파이프라인 개발</span><span class="sxs-lookup"><span data-stu-id="73849-102">Pipeline Development</span></span>
<span data-ttu-id="73849-103">추가 기능 파이프라인에는 서로 통신 하는 호스트 응용 프로그램 및 해당 추가 기능을 사용 해야 하는 파이프라인 세그먼트의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-103">The add-in pipeline is the path of pipeline segments that the host application and its add-in must use to communicate with each other.</span></span>  
  
 <span data-ttu-id="73849-104">다음 그림에서는 통신 파이프라인 및 해당 세그먼트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73849-104">The following illustration shows the communication pipeline and its segments.</span></span>  
  
 <span data-ttu-id="73849-105">![추가 &#45; 파이프라인 모델입니다. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="73849-105">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="73849-106">추가 기능 파이프라인</span><span class="sxs-lookup"><span data-stu-id="73849-106">Add-in pipeline</span></span>  
  
 <span data-ttu-id="73849-107">호스트 응용 프로그램 파이프라인의 한쪽 끝에 있고 다른 쪽 end에는 추가 기능에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73849-107">The host application is at one end of the pipeline and the add-in is at the other end.</span></span> <span data-ttu-id="73849-108">한쪽 끝에서 시작 하 고 가운데 방향으로 이동, 호스트 응용 프로그램과 추가 기능을 모두 공유 하는 개체 모델의 뷰를 정의 하는 추상 기본 클래스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-108">Starting from each end and moving toward the middle, both the host application and the add-in have an abstract base class that defines a view of the object model that they both share.</span></span> <span data-ttu-id="73849-109">이러한 형식 (클래스)은 보기에서 추가 기능 파이프라인 세그먼트 및 추가 기능 파이프라인 세그먼트의 [호스트] 보기를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-109">These types (classes) make up the add-in view pipeline segment and the host view of the add-in pipeline segment.</span></span> <span data-ttu-id="73849-110">뷰 추가 기능 파이프라인 세그먼트 종종 둘 이상의 추상 클래스를 포함 하지만 클래스에서 상속 되는 추가 기능에 추가 기능 기본 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-110">The add-in view pipeline segment often contains more than one abstract class but the class that the add-in inherits from is known as the add-in base.</span></span>  
  
 <span data-ttu-id="73849-111">추가 기능 측 어댑터 파이프라인 세그먼트 및 호스트 측 어댑터 파이프라인 세그먼트 convert 해당 뷰 파이프라인 세그먼트 사이의 계약 파이프라인 세그먼트 형식의 흐름.</span><span class="sxs-lookup"><span data-stu-id="73849-111">The add-in-side adapter pipeline segment and the host-side adapter pipeline segment convert the flow of types between their view pipeline segments and the contract pipeline segment.</span></span> <span data-ttu-id="73849-112">파이프라인의 중앙 세그먼트는 계약에서 파생 되는 <xref:System.AddIn.Contract.IContract> 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-112">The central segment of the pipeline is a contract that is derived from the <xref:System.AddIn.Contract.IContract> interface.</span></span> <span data-ttu-id="73849-113">이 계약은 호스트 응용 프로그램 및 해당 추가 기능에 둘 다를 사용 하는 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-113">This contract defines the methods that the host application and its add-in will both use.</span></span>  
  
 <span data-ttu-id="73849-114">개별 응용 프로그램 도메인에는 호스트와 추가 기능을 로드 하는 경우 추가 기능에 범위에서 호스트 응용 프로그램의 범위를 구분 하는 격리 경계를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-114">If you load the host and the add-in into separate application domains, you have an isolation boundary that separates the scope of the host application from the scope of the add-in.</span></span> <span data-ttu-id="73849-115">계약은 호스트와 추가 기능 응용 프로그램 도메인에 로드 된 어셈블리에만입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-115">The contract is the only assembly that is loaded in both the host and add-in application domains.</span></span> <span data-ttu-id="73849-116">호스트와 추가 기능을 각 계약 메서드의 해당 보기에만 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="73849-116">The host and the add-in each refer only to their view of the contract methods.</span></span> <span data-ttu-id="73849-117">계약에서 추상화 계층으로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-117">Therefore, they are separated by a layer of abstraction from the contract.</span></span>  
  
 <span data-ttu-id="73849-118">파이프라인 세그먼트를 개발 하려면 디렉터리 구조에 포함 될 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-118">To develop pipeline segments, you must create a directory structure that will contain them.</span></span> <span data-ttu-id="73849-119">개발 요구 사항 및 범위 지침에 대 한 자세한 내용은 참조 [파이프라인 개발 요구 사항](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-119">For more information about development requirements and scope guidelines, see [Pipeline Development Requirements](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
 <span data-ttu-id="73849-120">다음 그림은 파이프라인 세그먼트를 구성 하는 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73849-120">The following illustration shows the types that make up the pipeline segments.</span></span> <span data-ttu-id="73849-121">그림에 표시 된 형식의 이름이 임의적 이지만 정보 저장소를 생성 하는 방법으로 검색할 수 있도록 호스트와 호스트를 제외 하 고 모든 형식 보기 특성이 추가 기능에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-121">The names of the types shown in the illustration are arbitrary, but all types except for the host and the host view of the add-in require attributes so they can be discovered by methods that construct an information store.</span></span>  
  
 <span data-ttu-id="73849-122">![추가 &#45; 형식에 대 한 필수 특성이 있는 모델. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")</span><span class="sxs-lookup"><span data-stu-id="73849-122">![Add&#45;in model with required attributes on types.](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")</span></span>  
<span data-ttu-id="73849-123">추가 기능 파이프라인 형식</span><span class="sxs-lookup"><span data-stu-id="73849-123">Add-in pipeline with types</span></span>  
  
 <span data-ttu-id="73849-124">다음 표에서 추가 기능을 활성화 하는 데 파이프라인 세그먼트에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-124">The following table describes the pipeline segments for activating an add-in.</span></span> <span data-ttu-id="73849-125">이러한 세그먼트에 대 한 자세한 내용은 참조 [계약, 뷰 및 어댑터](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c)합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-125">For more information about these segments, see [Contracts, Views, and Adapters](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).</span></span>  
  
|<span data-ttu-id="73849-126">파이프라인 세그먼트</span><span class="sxs-lookup"><span data-stu-id="73849-126">Pipeline segment</span></span>|<span data-ttu-id="73849-127">설명</span><span class="sxs-lookup"><span data-stu-id="73849-127">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="73849-128">Host</span><span class="sxs-lookup"><span data-stu-id="73849-128">Host</span></span>|<span data-ttu-id="73849-129">응용 프로그램 어셈블리의 추가 기능 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73849-129">The application assembly that creates an instance of an add-in.</span></span>|  
|<span data-ttu-id="73849-130">추가 기능의 호스트 뷰</span><span class="sxs-lookup"><span data-stu-id="73849-130">Host view of the add-in</span></span>|<span data-ttu-id="73849-131">호스트 응용 프로그램의 뷰를 개체 형식 및 추가 기능으로 통신 하는 데 사용 되는 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73849-131">Represents the host application's view of the object types and methods used to communicate with the add-in.</span></span> <span data-ttu-id="73849-132">[호스트] 보기는 추상 기본 클래스 또는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-132">The host view is an abstract base class or interface.</span></span>|  
|<span data-ttu-id="73849-133">호스트 측 어댑터</span><span class="sxs-lookup"><span data-stu-id="73849-133">Host-side adapter</span></span>|<span data-ttu-id="73849-134">계약에서 메서드를 변경 하는 하나 또는 그 이상의 클래스가 있는 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-134">An assembly with one or more classes that adapts methods to and from the contract.</span></span><br /><br /> <span data-ttu-id="73849-135">이 파이프라인 세그먼트를 사용 하 여 식별 되는 <xref:System.AddIn.Pipeline.HostAdapterAttribute> 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-135">This pipeline segment is identified by using the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute.</span></span><br /><br /> <span data-ttu-id="73849-136">다중 모듈 어셈블리가 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73849-136">Multi-module assemblies are not supported.</span></span>|  
|<span data-ttu-id="73849-137">계약</span><span class="sxs-lookup"><span data-stu-id="73849-137">Contract</span></span>|<span data-ttu-id="73849-138">파생 된 인터페이스는 <xref:System.AddIn.Contract.IContract> 정의 하는 인터페이스 형식을 호스트와 해당 추가 기능에서 간에 통신 하기 위한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-138">An interface that is derived from the <xref:System.AddIn.Contract.IContract> interface and that defines the protocol for communicating types between the host and its add-in.</span></span><br /><br /> <span data-ttu-id="73849-139">이 파이프라인 세그먼트를 설정 하 여 식별 되는 <xref:System.AddIn.Pipeline.AddInContractAttribute> 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-139">This pipeline segment is identified by setting the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>|  
|<span data-ttu-id="73849-140">추가 기능 측 어댑터</span><span class="sxs-lookup"><span data-stu-id="73849-140">Add-in-side adapter</span></span>|<span data-ttu-id="73849-141">계약에서 메서드를 변경 하는 하나 또는 그 이상의 클래스가 있는 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-141">An assembly with one or more classes that adapts methods to and from the contract.</span></span><br /><br /> <span data-ttu-id="73849-142">이 파이프라인 세그먼트를 사용 하 여 식별 되는 <xref:System.AddIn.Pipeline.AddInAdapterAttribute> 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-142">This pipeline segment is identified by using the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute.</span></span><br /><br /> <span data-ttu-id="73849-143">각 어셈블리에 있는 형식을 포함 하는 추가 기능 측 어댑터 디렉터리는 <xref:System.AddIn.Pipeline.AddInAdapterAttribute> 특성에 대 한 추가 기능 응용 프로그램 도메인에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-143">Each assembly in the add-in-side adapter directory that contains a type that has an <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute is loaded into the add-in's application domain.</span></span><br /><br /> <span data-ttu-id="73849-144">추가 기능 측 디렉터리의 각 어셈블리는 자체 응용 프로그램 도메인에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-144">Each assembly in the add-in-side directory is loaded in its own application domain.</span></span><br /><br /> <span data-ttu-id="73849-145">다중 모듈 어셈블리가 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73849-145">Multi-module assemblies are not supported</span></span>|  
|<span data-ttu-id="73849-146">추가 기능에서 보기</span><span class="sxs-lookup"><span data-stu-id="73849-146">Add-in view</span></span>|<span data-ttu-id="73849-147">어셈블리에 대 한 추가 기능 뷰 개체 유형과 호스트와 통신 하는 데 사용 되는 메서드를 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-147">An assembly that represents the add-in's view of the object types and methods that are used to communicate with the host.</span></span> <span data-ttu-id="73849-148">추가 기능을 보기에는 추상 기본 클래스 또는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-148">The add-in view is an abstract base class or interface.</span></span><br /><br /> <span data-ttu-id="73849-149">이 파이프라인 세그먼트를 사용 하 여 식별 되는 <xref:System.AddIn.Pipeline.AddInBaseAttribute> 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-149">This pipeline segment is identified by using the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span><br /><br /> <span data-ttu-id="73849-150">각 어셈블리에 있는 형식을 포함 하는 AddInViews 디렉터리는 <xref:System.AddIn.Pipeline.AddInBaseAttribute> 특성에 대 한 추가 기능 응용 프로그램 도메인에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-150">Each assembly in the AddInViews directory that contains a type that has an <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute is loaded into the add-in's application domain.</span></span>|  
|<span data-ttu-id="73849-151">추가 기능</span><span class="sxs-lookup"><span data-stu-id="73849-151">Add-in</span></span>|<span data-ttu-id="73849-152">호스트에 대 한 서비스를 수행 하는 인스턴스화된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-152">An instantiated type that performs a service for the host.</span></span>|  
  
## <a name="pipeline-activation-path"></a><span data-ttu-id="73849-153">파이프라인 활성화 경로</span><span class="sxs-lookup"><span data-stu-id="73849-153">Pipeline Activation Path</span></span>  
 <span data-ttu-id="73849-154">다음 그림에서는 추가 기능을 활성화 될 때 형식의 활성화를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73849-154">The following illustration shows the activation of types when an add-in is activated.</span></span> <span data-ttu-id="73849-155">또한 개체를 전달 하는 계산 또는 개체의 컬렉션 결과 등 호스트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73849-155">It also shows the passing of objects to the host, such as the results of a calculation or a collection of objects.</span></span> <span data-ttu-id="73849-156">가장 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="73849-156">This is the most typical scenario.</span></span>  
  
 <span data-ttu-id="73849-157">![추가 &#45; 모델 활성화 경로 사용 합니다. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")</span><span class="sxs-lookup"><span data-stu-id="73849-157">![Add&#45;in model with activation path.](../../../docs/framework/add-ins/media/addin6.png "AddIn6")</span></span>  
<span data-ttu-id="73849-158">호스트에 추가 기능에서 활성화 경로</span><span class="sxs-lookup"><span data-stu-id="73849-158">Activation path from the add-in to the host</span></span>  
  
 <span data-ttu-id="73849-159">파이프라인의 활성화 경로 다음과 같이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-159">The activation path of the pipeline occurs as follows:</span></span>  
  
1.  <span data-ttu-id="73849-160">호스트 응용 프로그램에서 추가 기능 활성화는 <xref:System.AddIn.Hosting.AddInToken.Activate%2A> 메서드.</span><span class="sxs-lookup"><span data-stu-id="73849-160">The host application activates the add-in with the <xref:System.AddIn.Hosting.AddInToken.Activate%2A> method.</span></span>  
  
2.  <span data-ttu-id="73849-161">추가 기능, 추가 기능을 보기, 추가 기능 측 어댑터 및 계약 어셈블리에 대 한 추가 기능 응용 프로그램 도메인에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-161">The add-in, add-in view, add-in-side adapter, and the contract assemblies are loaded into the add-in's application domain.</span></span>  
  
3.  <span data-ttu-id="73849-162">추가 기능에서 보기를 사용 하 여 추가 기능 측 어댑터의 인스턴스를 만들 (로 식별 되는 클래스와는 <xref:System.AddIn.Pipeline.AddInBaseAttribute> 특성) 생성자로 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-162">An instance of the add-in-side adapter is created using the add-in view (with the class identified by the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute) as its constructor.</span></span> <span data-ttu-id="73849-163">추가 기능 측 어댑터는 계약에서 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-163">The add-in-side adapter inherits from the contract.</span></span>  
  
4.  <span data-ttu-id="73849-164">계약으로 형식화 된 추가 기능 측 어댑터 (선택 사항) 격리 경계를 넘어 호스트 측 어댑터 생성자로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-164">The add-in-side adapter, which is typed as the contract, is passed across the (optional) isolation boundary to the host-side adapter's constructor.</span></span>  
  
5.  <span data-ttu-id="73849-165">추가 기능, 호스트 측 어댑터와 계약 어셈블리의 [호스트] 보기에서 호스트 응용 프로그램 도메인에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-165">The host view of the add-in, host-side adapter, and the contract assemblies are loaded into the host's application domain.</span></span>  
  
6.  <span data-ttu-id="73849-166">호스트 측 어댑터의 인스턴스를 생성자로 계약을 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="73849-166">An instance of the host-side adapter is created using the contract as its constructor.</span></span> <span data-ttu-id="73849-167">호스트 측 어댑터의 추가 기능 [호스트] 보기에서 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73849-167">The host-side adapter inherits from the host view of the add-in.</span></span>  
  
7.  <span data-ttu-id="73849-168">추가 기능, 호스트는 추가 기능에 보고 하 고 해당 메서드 호출을 계속할 수 형식화 된 호스트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73849-168">The host has the add-in, which is typed as the host view of the add-in, and can continue calling its methods.</span></span>  
  
## <a name="walkthroughs"></a><span data-ttu-id="73849-169">연습</span><span class="sxs-lookup"><span data-stu-id="73849-169">Walkthroughs</span></span>  
 <span data-ttu-id="73849-170">Visual Studio를 사용 하 여 파이프라인을 만드는 방법을 설명 하는 연습 항목에서는 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73849-170">There are three walkthrough topics that describe how to create pipelines using Visual Studio:</span></span>  
  
-   [<span data-ttu-id="73849-171">연습: 확장 가능한 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="73849-171">Walkthrough: Creating an Extensible Application</span></span>](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     <span data-ttu-id="73849-172">계산기 추가 기능에 호스트에 대 한 더하기, 빼기, 곱하기 및 나누기 계산을 수행 하는 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-172">Describes a calculator add-in that performs addition, subtraction, multiplication, and divsion calculations for the host.</span></span>  
  
-   [<span data-ttu-id="73849-173">연습: 호스트 변경으로 이전 버전과 호환성을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="73849-173">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     <span data-ttu-id="73849-174">계산기 추가 기능을 향상 된 계산 기능 및 첫 번째는 계산기 추가 기능으로 호환성을 유지 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-174">Describes a calculator add-in with enhanced calculation capabilities, and how to maintain compatibility with the first calculator add-in.</span></span>  
  
-   [<span data-ttu-id="73849-175">연습: 호스트와 추가 기능 간에 컬렉션 전달</span><span class="sxs-lookup"><span data-stu-id="73849-175">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     <span data-ttu-id="73849-176">서 점 시나리오를 사용 하 여 파이프라인을 통해 데이터 컬렉션을 전달 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73849-176">Describes how to pass data collections over the pipeline using a book store scenario.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73849-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73849-177">See Also</span></span>  
 [<span data-ttu-id="73849-178">파이프라인 시나리오 추가 기능을</span><span class="sxs-lookup"><span data-stu-id="73849-178">Add-in Pipeline Scenarios</span></span>](http://msdn.microsoft.com/en-us/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [<span data-ttu-id="73849-179">추가 기능 및 확장성</span><span class="sxs-lookup"><span data-stu-id="73849-179">Add-ins and Extensibility</span></span>](../../../docs/framework/add-ins/index.md)