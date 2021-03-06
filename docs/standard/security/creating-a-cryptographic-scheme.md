---
title: 암호화 체계 만들기
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197895"
---
# <a name="creating-a-cryptographic-scheme"></a>암호화 체계 만들기
.NET Framework의 암호화 구성 요소를 결합하여 다양한 체계를 만들고 데이터를 암호화 및 암호 해독할 수 있습니다.  
  
 데이터 암호화 및 암호 해독을 위한 간단한 암호화 체계에서는 다음 단계를 지정할 수 있습니다.  
  
1.  각 당사자가 공개/개인 키 쌍을 생성합니다.  
  
2.  양쪽 당사자가 공개 키를 교환합니다.  
  
3.  예를 들어 각 당사자가 TripleDES 암호화를 위한 비밀 키를 생성하고 상대방의 공개 키를 사용하여 새로 만든 키를 암호화합니다.  
  
4.  각 당사자가 상대방에게 데이터를 보내고 상대방의 비밀 키와 자신의 비밀 키를 특정 순서로 결합하여 새 비밀 키를 만듭니다.  
  
5.  양쪽 당사자가 대칭 암호화를 사용하여 대화를 시작합니다.  
  
 암호화 체계를 만드는 과정은 간단한 작업이 아닙니다. 암호화를 사용 하는 방법은 Platform SDK 설명서의 암호화 항목을 참조 하세요. http://msdn.microsoft.com/library합니다.  
  
## <a name="see-also"></a>참고자료

- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
