---
title: Vytváření knihovny DLL pouze prostředků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea6590a57a336740be0a9439c959ebe32239d4e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703454"
---
# <a name="creating-a-resource-only-dll"></a>Vytvoření knihovny DLL obsahující pouze prostředky

Knihovny DLL pouze prostředků je knihovnu DLL, která obsahuje prostředky, jako jsou ikony, bitmapy, řetězce a dialogová okna. Použití knihovny DLL pouze prostředků je dobrým způsobem, jak sdílet stejnou sadu prostředků mezi více aplikacemi. Je také vhodný způsob aplikace s prostředky lokalizovanými pro více jazyků (viz [lokalizované prostředky v aplikacích MFC: satelitní knihovny DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)).

Pokud chcete vytvořit knihovnu DLL pouze prostředků, vytvořte nový projekt Win32 DLL (non-MFC) a přidat prostředky do projektu.

- Vyberte projekt Win32 v **nový projekt** dialogové okno a zadejte typ projektu knihovny DLL v Průvodci vytvořením projektu Win32.

- Vytvořte nový skript prostředků, která obsahuje prostředky (například řetězce nebo nabídka) pro knihovnu DLL a uložte soubor .rc.

- Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**a pak vloží nový soubor .rc do projektu.

- Zadejte [NOENTRY](../build/reference/noentry-no-entry-point.md) – možnost linkeru. / NOENTRY brání linkeru v propojení odkazu na `_main` do knihovny DLL; tato možnost je vyžadována pro vytvoření knihovny DLL pouze prostředků.

- Sestavení knihovny DLL.

Aplikace, která používá knihovnu DLL pouze prostředků by měly volat [LoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) pro explicitní propojení ke knihovně DLL. Přístup k prostředkům, volání obecné funkce `FindResource` a `LoadResource`, pracovat na libovolný typ prostředku nebo volání jednoho z následujících funkcí specifických pro prostředky:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

Aplikace by měly volat `FreeLibrary` po dokončení používání prostředků.

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)