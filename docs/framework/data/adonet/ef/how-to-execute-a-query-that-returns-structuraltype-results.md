---
title: '방법: StructuralType 결과를 반환하는 쿼리 실행'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 1a53ab6ab455975f0597eab76aeaa2db3ffd42a3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182387"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a>방법: StructuralType 결과를 반환하는 쿼리 실행
이 항목에서는 <xref:System.Data.EntityClient.EntityCommand> 개체를 사용하여 개념적 모델에 대해 명령을 실행하는 방법과 <xref:System.Data.Metadata.Edm.StructuralType>를 사용하여 <xref:System.Data.EntityClient.EntityDataReader> 결과를 검색하는 방법을 보여 줍니다. <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> 및 <xref:System.Data.Metadata.Edm.ComplexType> 클래스는 <xref:System.Data.Metadata.Edm.StructuralType> 클래스에서 파생됩니다.  
  
### <a name="to-run-the-code-in-this-example"></a>이 예제의 코드를 실행하려면  
  
1.  추가 합니다 [AdventureWorks Sales 모델](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) 프로젝트에 사용 하도록 프로젝트를 구성 하 고는 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]합니다. 자세한 내용은 [방법: 엔터티 데이터 모델 마법사를 사용 하 여](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)입니다.  
  
2.  응용 프로그램의 코드 페이지에서 다음 `using` 문(Visual Basic에서는 `Imports`)을 추가합니다.  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>예제  
 이 예제에서는 <xref:System.Data.Metadata.Edm.EntityType> 결과를 반환하는 쿼리를 실행합니다. 다음 쿼리를 `ExecuteStructuralTypeQuery` 함수에 인수로 전달하면 이 함수는 `Products`에 대한 정보를 표시합니다.  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 다음과 같은 매개 변수가 있는 쿼리를 전달하는 경우 <xref:System.Data.EntityClient.EntityParameter> 개체를 <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> 개체의 <xref:System.Data.EntityClient.EntityCommand> 속성에 추가합니다.  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a>참고 항목  
 [엔터티 SQL 참조](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity Framework용 EntityClient 공급자](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
