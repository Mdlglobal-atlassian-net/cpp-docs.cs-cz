---
title: Předdefinované symboly systému Win32 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18edb56c03541f61607817d14fdbadb067a3630d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422776"
---
# <a name="win32-predefined-symbols"></a>Předdefinované symboly systému Win32

Tyto symboly jsou definovány v souborech hlaviček Win32 a podporují standardní funkce aplikace Windows a akce. Tyto symboly se používá hlavně s společné prvky uživatelského rozhraní. Při práci s ovládacími prvky v editoru prostředků, zobrazí se tyto symboly v [okno vlastností](/visualstudio/ide/reference/properties-window) přidružené k běžné ovládací prvky. Například pokud vaše nástrojů by měl zobrazit ikonu aplikace, na ikonu se přidruží symbol IDI_SMALL v **okně s vlastnostmi**.

|||
|-|-|
|IDABORT|Ovládacího prvku: Tlačítko Přerušit pole dialogového okna|
|IDC_STATIC|Ovládací prvek: Statický text v dialogovém okně|
|IDCANCEL|Ovládacího prvku: Tlačítko Storno pole dialogového okna|
|IDD_ABOUTBOX|Dialogové okno: Produktu dialogové okno|
|IDI_PROJECTNAME|Ikona: Aktuální ikony projektu|
|IDI_SMALL|Ikona: Aktuální projekt malé ikony|
|IDIGNORE|Ovládací prvek: Používá se ignorovat tlačítka v dialogových oknech|
|IDM_ABOUT|Položka nabídky: Používá s nápovědou... O...|
|IDM_EXIT|Položka nabídky: Používá se soubor... Ukončení...|
|IDNO|Ovládací prvek: Dialogové okno se neobjeví tlačítko|
|IDOK|Ovládacího prvku: Tlačítko pole OK dialogového okna|
|IDRETRY|Ovládacího prvku: Tlačítko Opakovat pole dialogového okna|
|IDS_APP_TITLE|Řetězec: Název aktuální aplikace|
|IDYES|Ovládací prvek: Dialogové okno Ano tlačítko.|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)