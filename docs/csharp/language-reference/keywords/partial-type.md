---
title: partial 형식(C# 참조)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 365d00d2c53d3efe1cd4330bdd3ec48740a49c53
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187057"
---
# <a name="partial-type-c-reference"></a>partial 형식(C# 참조)

부분 형식(Partial Type) 정의를 사용하면 클래스, 구조체 또는 인터페이스의 정의를 여러 파일로 분할할 수 있습니다.

*File1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

*File2.cs*에서 선언은 다음과 같습니다.

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>설명

클래스, 구조체 또는 인터페이스 형식을 여러 파일에 분할하면 대형 프로젝트 또는 [Windows Forms 디자이너](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)에서 제공하는 것과 같은 자동으로 생성된 코드로 작업할 때 유용할 수 있습니다. 부분 형식(Partial Type)에는 [부분 메서드(Partial Method)](partial-method.md)가 포함될 수 있습니다. 자세한 내용은 참조 [Partial 클래스 및 메서드](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)합니다.

## <a name="c-language-specification"></a>C# 언어 사양

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 프로그래밍 가이드](../../programming-guide/index.md)
- [한정자](modifiers.md)
- [제네릭 소개](../../programming-guide/generics/introduction-to-generics.md)