---
title: Předdefinované symboly ATL
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: 16991746c5c858310466f7eebd91a8478d2dcc5c
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954845"
---
# <a name="atl-predefined-symbols"></a>Předdefinované symboly ATL

Tyto symboly jsou definovány v souborech hlaviček knihovny ATL, ale podporují standardní funkce aplikace Windows a akce. Tyto symboly se používá hlavně s dialogových oknech.

Pokud pracujete s ovládacími prvky a dialogy v [editoru dialogového okna](../windows/dialog-editor.md), tyto symboly se zobrazí v **vlastnosti** okno, které jsou přidružené k běžné ovládací prvky. Například pokud má vaše dialogové okno **zrušit** tlačítko, zda příkaz bude spojená s symbol IDCANCEL v [okno vlastností](/visualstudio/ide/reference/properties-window).

|||
|-|-|
|IDABORT|(ovládací prvek) Dialogové okno, tlačítko Přerušit|
|IDC_STATIC|(ovládací prvek) Statický ovládací prvek|
|IDCANCEL|(ovládací prvek) Dialogové okno, tlačítko Storno.|
|IDIGNORE|(ovládací prvek) Dialogové okno, tlačítko Ignorovat|
|IDNO|(ovládací prvek) Dialogové okno, se neobjeví tlačítko|
|IDOK|(ovládací prvek) Dialogové okno, tlačítko OK|
|IDR_ACCELERATOR1|(prostředků) Tabulky akcelerátorů|
|IDRETRY|(ovládací prvek) Dialogové okno, tlačítko opakování|
|IDS_PROJNAME|(string) Aktuální název aplikace|
|IDYES|(ovládací prvek) Dialogové okno, tlačítko Ano|

## <a name="requirements"></a>Požadavky

ATL

## <a name="see-also"></a>Viz také

[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
[Předdefinované symboly MFC](../windows/mfc-predefined-symbols.md)<br/>
[Předdefinované symboly systému Win32](../windows/win32-predefined-symbols.md)<br/>