---
title: "Dialogové okno Přidání ovládacích prvků do dialogového okna způsobí nefunkčnost | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], troubleshooting
- common controls, troubleshooting
- troubleshooting controls
- dialog boxes, troubleshooting
- dialog box controls, troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0ec4825419c7a9d3c9bc35151b84c327a03325b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Přidání ovládacích prvků do dialogového okna způsobí nefunkčnost okna.
Po přidání do běžného ovládacího prvku nebo ovládacího prvku RichEdit do dialogového okna, nebude se zobrazovat při testování dialogové okno nebo dialogové okno samotné se nezobrazí.  
  
 **Příklad problému**  
  
1.  Vytvoření projektu Win32, úprava nastavení aplikace, takže vytvořit aplikaci pro Windows (ne konzolovou aplikaci).  
  
2.  V [zobrazení prostředků](../windows/resource-view-window.md), dvakrát klikněte na soubor.  
  
3.  V dialogovém okně Možnosti, dvakrát klikněte **o** pole.  
  
4.  Přidat **ovládací prvek adresy IP** do dialogového okna.  
  
5.  Uložte a **znovu vytvořit všechny**.  
  
6.  Spuštění programu.  
  
7.  Na dialogových oken **pomoci** nabídky, klikněte na tlačítko **o** příkaz; žádné dialogové okno bude zobrazeno.  
  
 **Příčinu**  
  
 V současné době editoru dialogových oken nepřidá automaticky kódu do projektu při můžete přetáhnout následující běžné ovládací prvky nebo ovládacích prvků do dialogového okna pro úpravy s formátováním. Ani v sadě Visual Studio poskytuje chybě nebo upozornění při výskytu tohoto problému. Kód pro ovládací prvek je musí přidat ručně.  
  
||||  
|-|-|-|  
|Posuvník|Ovládací prvek stromu|Výběr data a času|  
|Ovládací prvek typu číselník|Ovládací prvek karty|Měsíční kalendář|  
|Ovládací prvek průběh|Ovládacího prvku animace|Ovládací prvek adresy IP|  
|Klávesové zkratky|Ovládací prvek pro úpravy s formátováním|Rozšířená pole se seznamem|  
|Ovládací prvek seznamu|Ovládací prvek pro úpravy s formátováním 2.0|Vlastní ovládací prvek|  
  
## <a name="the-fix-for-common-controls"></a>Opravu pro běžné ovládací prvky  
 Abyste mohli používat běžné ovládací prvky v dialogovém okně, je třeba volat [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) nebo **AFXInitCommonControls** předtím, než vytvoříte dialogové okno.  
  
## <a name="the-fix-for-richedit-controls"></a>Opravu pro RichEdit ovládací prvky  
 Je třeba volat **LoadLibrary** pro ovládací prvky rich edit. Další informace najdete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)], a [– Přehled ovládacího prvku upravit bohaté](../mfc/overview-of-the-rich-edit-control.md).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s editoru dialogových oken](../windows/troubleshooting-the-dialog-editor.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)

