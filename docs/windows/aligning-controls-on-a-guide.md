---
title: Zarovnání ovládacích prvků podle vodítka | Microsoft Docs
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
ms.openlocfilehash: a7c8cc57b4d2e7150ff09858cfd5b315beb37962
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857835"
---
# <a name="aligning-controls-on-a-guide"></a>Zarovnání ovládacích prvků podle vodítka
Úchyty ovládacích prvků Přichytit k vodítkům, když se přesouvají ovládací prvky a příručky Přichytit k ovládacím prvkům (pokud neexistují žádná opatření dříve přichyceno k průvodci). Po přesunu Průvodce je také přesunout ovládacích prvků, které jsou přichytávány k němu. Když je přesunut jeden příručky, změní se velikost ovládací prvky přichyceno k více než jeden průvodce.  
  
 Značky v pravítek, které určuje mezery mezi příručky a ovládací prvky jsou definovány jednotky dialogu (dlu). DLU je založena na velikosti písma pole dialogové okno, obvykle 8 bodů MS prostředí, dialogové okno. Vodorovné DLU je průměrná velikost písma dialogové okno pole dělený čtyři. Svislé DLU je průměrná výška písmo dělený 8.  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>Chcete-li velikost skupinu ovládacích prvků podle vodítka  
  
1.  Přichytit k Průvodce jedné straně ovládacího prvku (nebo ovládací prvky).  
  
2.  Přetáhněte vodítko na druhé straně ovládacího prvku (nebo ovládací prvky).  
  
     V případě potřeby s více ovládacích prvků, velikost každé Přichytit k Průvodci druhý.  
  
3.  Přesuňte buď Průvodce velikost ovládacího prvku (nebo ovládací prvky).  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>Chcete-li změnit intervalů značek  
  
1.  Z **formátu** nabídce zvolte **nastavení průvodce**.  
  
2.  V [dialogové okno nastavení průvodce](../windows/guide-settings-dialog-box.md)v **rozteč mřížky** pole, zadejte v dlu novou šířku a výšku.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Stavy editoru dialogových oken (vodítka a mřížky)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)

