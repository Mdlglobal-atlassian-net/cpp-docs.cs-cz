---
title: Nastavení šířky vodorovného posuvníku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls, scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars, displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars, width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54b68ec8f780fc8022543813b412eaff2045cbdf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645601"
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>Nastavení šířky vodorovného posuvníku
Když přidáte seznam s vodorovný posuvník do dialogového okna pomocí tříd knihovny MFC, posuvník nezobrazí automaticky ve vaší aplikaci.  
  
### <a name="to-make-the-scroll-bar-appear"></a>Chcete-li posuvník  
  
1.  Nastavte maximální šířku prvku nejširší voláním [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) ve vašem kódu.  
  
     Bez této sady hodnot posuvník nezobrazí, i když jsou položky v seznamu širší než pole.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)