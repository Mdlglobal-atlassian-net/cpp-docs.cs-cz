---
title: Přidání ovládacích prvků do dialogového okna způsobí, že dialogové okno přestane fungovat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0b2ecb47c17aeeda1cfd54c19cb72d0d1808a836
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647115"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Přidání ovládacích prvků do dialogového okna způsobí nefunkčnost okna.
Po přidání běžného ovládacího prvku nebo ovládací prvek RTF do dialogového okna, nebude se zobrazovat při testování dialogových oken nebo dialogového okna, samotné se nezobrazí.  
  
### <a name="example-of-the-problem"></a>Příklad problému  
  
1.  Vytvořte projekt Win32, změna nastavení aplikace, proto vytvořit aplikace Windows (ne konzolovou aplikaci).  
  
2.  V [zobrazení prostředků](../windows/resource-view-window.md), dvakrát klikněte na soubor .rc.  
  
3.  V části Možnosti dialogového okna, dvakrát klikněte **o** pole.  
  
4.  Přidat **ovládací prvek adresy IP** do dialogového okna.  
  
5.  Uložit a **sestavit vše znovu**.  
  
6.  Spuštění programu.  
  
7.  V dialogových oken **pomáhají** nabídky, klikněte na tlačítko **o** příkaz; žádné dialogové okno zobrazí okno.  
  
### <a name="the-cause"></a>Příčinu  
  
 V současné době editor dialogového okna automaticky nedojde k přidání kódu do projektu při přetažení následující běžné ovládací prvky nebo ovládací prvky na dialogové okno pro úpravy s formátováním. Ani sada Visual Studio poskytuje chybu nebo upozornění při výskytu tohoto problému. Kód pro ovládací prvek musí přidat ručně.  
  
||||  
|-|-|-|  
|Ovládací prvek posuvníku|Ovládací prvek stromu|Výběr data a času|  
|Ovládací prvek typu číselník|Ovládací prvek karty|Měsíční kalendář|  
|Ovládací prvek průběh|Animace ovládacího prvku|Ovládací prvek adresy IP|  
|Klávesová zkratka|Ovládací prvek pro úpravy s formátováním|Rozšířené pole se seznamem|  
|Ovládací prvek seznamu|Ovládací prvek pro úpravy s formátováním 2.0|Vlastní ovládací prvek|  
  
## <a name="the-fix-for-common-controls"></a>Oprava pro běžné ovládací prvky  
 Chcete-li použít běžné ovládací prvky v dialogovém okně, je třeba volat [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) nebo `AFXInitCommonControls` předtím, než vytvoříte dialogové okno.  
  
## <a name="the-fix-for-richedit-controls"></a>Oprava pro ovládací prvky RichEdit  
 Je nutné volat `LoadLibrary` pro ovládací prvky pro úpravy s formátováním. Další informace najdete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)], a [– Přehled ovládacího prvku Rich upravit](../mfc/overview-of-the-rich-edit-control.md).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s editorem dialogového okna](../windows/troubleshooting-the-dialog-editor.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)