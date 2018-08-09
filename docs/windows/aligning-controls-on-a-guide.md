---
title: Zarovnání ovládacích prvků podle vodítka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog editor, snap to guides
- guides, tick mark interval
- dialog box controls, placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a1a586a3a17e829d883dff96c12f6a2fdabe669f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643855"
---
# <a name="aligning-controls-on-a-guide"></a>Zarovnání ovládacích prvků podle vodítka
Úchyty pro změnu velikosti ovládacích prvků Přichytit k vodítkům při přesunutí ovládacích prvků a příručky Přichytit k ovládacím prvkům (pokud neexistují žádná opatření dříve přichycená k průvodci). Když průvodce se přesune, ovládací prvky, které jsou přichycená k němu také přesunout. Ovládací prvky přichycená k více než jeden Průvodce se mění velikost, pokud jeden z příručky přesunuta.  
  
 Značky v pravítka, která určují mezery v průvodci a ovládací prvky jsou definovány jednotky dialogu (dlu). DLU vychází z velikosti pole písmo dialogového okna, obvykle 8 bodu MS Shell Dlg. Vodorovné DLU je průměrná délka pole písmo dialogového okna dělený čtyři. Svislé DLU je průměrná výška písmo dělený osmidílné série.  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>Chcete-li velikost skupiny ovládacích prvků podle vodítka  
  
1.  Přichytit k vodítko straně ovládacího prvku (nebo ovládací prvky).  
  
2.  Přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky).  
  
     V případě potřeby s více ovládacích prvků, velikost každého se přichytil k druhé průvodce.  
  
3.  Přesuňte buď Průvodce pro nastavení velikosti ovládacího prvku (nebo ovládací prvky).  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>Chcete-li změnit intervalech osové značky  
  
1.  Z **formátu** nabídce zvolte **nastavení vodítek**.  
  
2.  V [dialogové okno nastavení průvodce](../windows/guide-settings-dialog-box.md)v **rozteč mřížky** v dlu zadejte novou šířku a výšku.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Stavy editoru dialogových oken (vodítka a mřížky)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)