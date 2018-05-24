### <a name="unexpected-invalidcastexception-from-invokemethod-activity-in-wf4"></a><span data-ttu-id="a14a0-101">WF4의 InvokeMethod 작업에서 예기치 않은 InvalidCastException이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a14a0-101">Unexpected InvalidCastException from InvokeMethod activity in WF4</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a14a0-102">설명</span><span class="sxs-lookup"><span data-stu-id="a14a0-102">Details</span></span>|<span data-ttu-id="a14a0-103">null 허용(nullable) 매개 변수가 있는 메서드를 대상으로 하는 <xref:System.Activities.Statements.InvokeMethod>를 사용하면 <xref:System.InvalidCastException?displayProperty=name>을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="a14a0-103">Using a <xref:System.Activities.Statements.InvokeMethod> that targets a method with a nullable parameter can throw an <xref:System.InvalidCastException?displayProperty=name>.</span></span>|
|<span data-ttu-id="a14a0-104">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="a14a0-104">Suggestion</span></span>|<span data-ttu-id="a14a0-105">이 동작은 .NET Framework 4.5 서비스 릴리스에서 되돌려졌습니다.</span><span class="sxs-lookup"><span data-stu-id="a14a0-105">This behavior was reverted in a .NET Framework 4.5 servicing release.</span></span> <span data-ttu-id="a14a0-106">이 문제를 해결하려면 .NET Framework 4.5를 업데이트하거나 .NET Framework 4.5.1 이상으로 업그레이드하세요.</span><span class="sxs-lookup"><span data-stu-id="a14a0-106">Please update the .NET Framework 4.5 (or upgrade to .NET Framework 4.5.1 or later) to fix the issue.</span></span>|
|<span data-ttu-id="a14a0-107">범위</span><span class="sxs-lookup"><span data-stu-id="a14a0-107">Scope</span></span>|<span data-ttu-id="a14a0-108">부</span><span class="sxs-lookup"><span data-stu-id="a14a0-108">Minor</span></span>|
|<span data-ttu-id="a14a0-109">버전</span><span class="sxs-lookup"><span data-stu-id="a14a0-109">Version</span></span>|<span data-ttu-id="a14a0-110">4.5</span><span class="sxs-lookup"><span data-stu-id="a14a0-110">4.5</span></span>|
|<span data-ttu-id="a14a0-111">형식</span><span class="sxs-lookup"><span data-stu-id="a14a0-111">Type</span></span>|<span data-ttu-id="a14a0-112">런타임</span><span class="sxs-lookup"><span data-stu-id="a14a0-112">Runtime</span></span>|
|<span data-ttu-id="a14a0-113">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="a14a0-113">Affected APIs</span></span>|<ul><li><xref:System.Activities.Statements.InvokeMethod.Parameters?displayProperty=nameWithType></li></ul>|
|<span data-ttu-id="a14a0-114">분석기</span><span class="sxs-lookup"><span data-stu-id="a14a0-114">Analyzers</span></span>|<ul><li><span data-ttu-id="a14a0-115">CD0088</span><span class="sxs-lookup"><span data-stu-id="a14a0-115">CD0088</span></span></li></ul>|
