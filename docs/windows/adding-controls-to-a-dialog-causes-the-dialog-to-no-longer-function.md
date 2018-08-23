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
ms.openlocfilehash: 9c1cb1a1894f3288e2825c5eb7d521a468ccdfa7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592811"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Přidání ovládacích prvků do dialogového okna způsobí nefunkčnost okna.

Po přidání běžného ovládacího prvku nebo ovládací prvek RTF do dialogového okna, nebude se zobrazovat při testování dialogových oken nebo dialogového okna, samotné se nezobrazí.

### <a name="example-of-the-problem"></a>Příklad problému

1. Vytvořte projekt Win32, změna nastavení aplikace, proto vytvořit aplikace Windows (ne konzolovou aplikaci).

2. V [zobrazení prostředků](../windows/resource-view-window.md), dvakrát klikněte na soubor .rc.

3. V části Možnosti dialogového okna, dvakrát klikněte **o** pole.

4. Přidat **ovládací prvek adresy IP** do dialogového okna.

5. Uložit a **sestavit vše znovu**.

6. Spuštění programu.

7. V dialogových oken **pomáhají** nabídky, klikněte na tlačítko **o** příkaz; žádné dialogové okno zobrazí okno.

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

Je nutné volat `LoadLibrary` pro ovládací prvky pro úpravy s formátováním. Další informace najdete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) v sadě Windows SDK a [– Přehled ovládacího prvku Rich upravit](../mfc/overview-of-the-rich-edit-control.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Řešení potíží s editorem dialogového okna](../windows/troubleshooting-the-dialog-editor.md)  
[Editor dialogových oken](../windows/dialog-editor.md)