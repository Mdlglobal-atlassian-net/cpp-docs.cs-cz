---
title: Předdefinované symboly systému Win32
ms.date: 02/14/2019
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
ms.openlocfilehash: 8a238021f255da30a132755a297a471dd1f51246
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024939"
---
# <a name="win32-predefined-symbols"></a>Předdefinované symboly systému Win32

Tyto symboly jsou definovány v souborech hlaviček Win32 a podporují standardní funkce aplikace Windows a akce. Tyto symboly se používá hlavně s společné prvky uživatelského rozhraní. Při práci s ovládacími prvky v editoru prostředků, zobrazí se tyto symboly v [okno vlastností](/visualstudio/ide/reference/properties-window) přidružené k běžné ovládací prvky. Například pokud vaše nástrojů by měl zobrazit ikonu aplikace, na ikonu se přidruží symbol IDI_SMALL v **vlastnost** okna.

|||
|-|-|
|IDABORT|(ovládací prvek) Dialogové okno, tlačítko Přerušit|
|IDC_STATIC|(ovládací prvek) Statický text v dialogovém okně|
|IDCANCEL|(ovládací prvek) Dialogové okno, tlačítko Storno.|
|IDD_ABOUTBOX|(dialogového okna) Dialogové okno o produktu|
|IDI_PROJECTNAME|(ikona) Aktuální ikony projektu|
|IDI_SMALL|(ikona) Aktuální projekt malé ikony|
|IDIGNORE|(ovládací prvek) Použít s ignorovat tlačítka v dialogových oknech|
|IDM_ABOUT|(položka nabídky) Použít s nápovědou... O...|
|IDM_EXIT|(položka nabídky) Používá se soubor... Ukončení...|
|IDNO|(ovládací prvek) Dialogové okno, se neobjeví tlačítko|
|IDOK|(ovládací prvek) Dialogové okno, tlačítko OK|
|IDRETRY|(ovládací prvek) Dialogové okno, tlačítko opakování|
|IDS_APP_TITLE|(string) Aktuální název aplikace|
|IDYES|(ovládací prvek) Dialogové okno, tlačítko Ano|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
[Předdefinované symboly MFC](../windows/mfc-predefined-symbols.md)<br/>
[Předdefinované symboly ATL](../windows/atl-predefined-symbols.md)<br/>