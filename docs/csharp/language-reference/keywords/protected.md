---
title: protected 키워드(C# 참조)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f25e692430f876ec384971079d6d0aa2c97e967b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44197882"
---
# <a name="protected-c-reference"></a>protected(C# 참조)

`protected` 키워드는 멤버 액세스 한정자입니다.

 > 이 페이지에서는 `protected` 액세스를 설명합니다. `protected` 키워드는 [`protected internal`](protected-internal.md) 및 [`private protected`](private-protected.md) 액세스 한정자의 일부이기도 합니다.

protected 멤버는 해당 클래스 내에서 파생 클래스 인스턴스가 액세스할 수 있습니다.

`protected` 및 다른 액세스 한정자와 비교는 [액세스 가능성 수준](accessibility-levels.md)을 참조하세요.

## <a name="example"></a>예

기본 클래스의 protected 멤버는 파생 클래스 형식을 통해 액세스가 발생하는 경우에만 파생 클래스에서 액세스할 수 있습니다. 예를 들어 다음 코드 세그먼트를 고려하세요.

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

`a.x = 10` 문은 정적 메서드 Main 내에서 작성되었으며 클래스 B의 인스턴스가 아니므로 오류를 생성합니다.

구조체를 상속할 수 없기 때문에 구조체 멤버는 보호할 수 없습니다.

## <a name="example"></a>예

이 예제에서 `DerivedPoint` 클래스는 `Point`에서 파생됩니다. 따라서 파생 클래스에서 직접 기본 클래스의 protected 멤버를 액세스할 수 있습니다.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

`x` 및 `y`의 액세스 수준을 [private](private.md)로 변경하는 경우 컴파일러가 오류 메시지를 실행합니다.

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>C# 언어 사양

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>참고 항목

- [C# 참조](../../../csharp/language-reference/index.md)
- [C# 프로그래밍 가이드](../../../csharp/programming-guide/index.md)
- [C# 키워드](index.md)
- [액세스 한정자](access-modifiers.md)
- [액세스 수준](accessibility-levels.md)
- [한정자](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [internal virtual 키워드에 대한 보안 문제](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))