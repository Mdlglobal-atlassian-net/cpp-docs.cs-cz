---
title: Předdefinované symboly ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 965eb339295b86c223b5081dede8e33dd282b95d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386597"
---
# <a name="atl-predefined-symbols"></a>Předdefinované symboly ATL

Tyto symboly jsou definovány v souborech hlaviček knihovny ATL, ale podporují standardní funkce aplikace Windows a akce. Tyto symboly se používá hlavně s dialogových oknech. Pokud pracujete s ovládacími prvky a dialogy v [editoru dialogového okna](../windows/dialog-editor.md), tyto symboly se zobrazí v **vlastnosti** okno, které jsou přidružené k běžné ovládací prvky. Například pokud má vaše dialogové okno **zrušit** tlačítko, zda příkaz bude spojená s symbol IDCANCEL v [okno vlastností](/visualstudio/ide/reference/properties-window).

|||
|-|-|
|IDABORT|Ovládacího prvku: Tlačítko Přerušit pole dialogového okna|
|IDC_STATIC|Ovládacího prvku: Statický ovládací prvek|
|IDCANCEL|Ovládacího prvku: Tlačítko Storno pole dialogového okna|
|IDIGNORE|Ovládacího prvku: Tlačítko Ignorovat pole dialogového okna|
|IDNO|Ovládací prvek: Dialogové okno se neobjeví tlačítko|
|IDOK|Ovládacího prvku: Tlačítko pole OK dialogového okna|
|IDR_ACCELERATOR1|Prostředků: Tabulky akcelerátoru|
|IDRETRY|Ovládacího prvku: Tlačítko Opakovat pole dialogového okna|
|IDS_PROJNAME|Řetězec: Název aktuální aplikace|
|IDYES|Ovládací prvek: Dialogové okno Ano tlačítko.|

## <a name="requirements"></a>Požadavky

ATL

## <a name="see-also"></a>Viz také

[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)