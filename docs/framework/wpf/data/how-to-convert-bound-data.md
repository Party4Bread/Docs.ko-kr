---
title: '방법: 바인딩된 데이터 변환'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556642"
---
# <a name="how-to-convert-bound-data"></a>방법: 바인딩된 데이터 변환
이 예제에서는 바인딩에 사용 되는 데이터에 변환을 적용 하는 방법을 보여 줍니다.  
  
 데이터 바인딩 중으로 변환 하려면 구현 하는 클래스 만들어야 합니다는 <xref:System.Windows.Data.IValueConverter> 포함 된 인터페이스는 <xref:System.Windows.Data.IValueConverter.Convert%2A> 및 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 메서드.  
  
## <a name="example"></a>예제  
 다음 예제에는 연도, 월 및 일만 표시 되도록에 전달 되는 날짜 값을 변환 하는 날짜 변환기의 구현을 보여 줍니다. 구현 하는 경우는 <xref:System.Windows.Data.IValueConverter> 인터페이스를 사용 하 여 구현을 데코 레이트 하는 것이 좋습니다는는 <xref:System.Windows.Data.ValueConversionAttribute> 개발에 알리기 위해 특성 도구는 다음 예제 에서처럼 변환과 관련 된 데이터 형식:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 변환기를 만든 후에 리소스로 추가할 수 있습니다 프로그램 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 파일입니다. 다음 예에서 *src* 는 네임 스페이스로 매핑되면 *DateConverter* 정의 됩니다.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 마지막으로 다음 구문을 사용 하 여 바인딩을에서 변환기를 사용할 수 있습니다. 다음 예제에서는 텍스트의 콘텐츠는 <xref:System.Windows.Controls.TextBlock> 에 바인딩된 *StartDate*, 외부 데이터 원본의 속성인 합니다.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 위의 예제에서 참조 된 스타일 리소스는이 항목에 표시 되지 않은 리소스 섹션에 정의 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [바인딩 유효성 검사 구현](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [데이터 바인딩 개요](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [방법 항목](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
