---
title: Prostředek zahrnuje dialogové okno (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourceincludes
helpviewer_keywords:
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
ms.openlocfilehash: b0e7125e07deb965055da54126eb0933e64c0429
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625056"
---
# <a name="resource-includes-dialog-box-c"></a>Prostředek zahrnuje dialogové okno (C++)

Můžete použít **prostředek zahrnuje** dialogové okno projektu v jazyce C++ upravit prostředí normální funkční uspořádání ukládání všech prostředků v projektu soubor .rc a všechny [symboly](../windows/symbols-resource-identifiers.md) v souboru Resource.h.

Chcete-li otevřít **prostředek zahrnuje** dialogové okno, klikněte pravým tlačítkem na příslušný .rc souborů v [zobrazení prostředků](../windows/resource-view-window.md), klikněte na tlačítko **prostředek zahrnuje** z místní nabídky.

- **Hlavičkový soubor symbolů**

   Umožňuje změnit název hlavičkového souboru, kde jsou uloženy definice symbolů pro váš soubor prostředků. Další informace najdete v tématu [mění se názvy z hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md).

- **Směrnice souborů jen pro čtení**

   Umožňuje zahrnout soubory hlaviček, které obsahují symboly, které by se nemělo upravovat během úprav relace. Například můžete zahrnout soubor se symboly, jež jsou sdílena mezi několika projekty. Můžete také zahrnout soubory hlaviček knihovny MFC. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md).

- **Směrnice času kompilace**

   Umožňuje zahrnout soubory prostředků, které vytvářejí se a upravují samostatně z prostředků v hlavní soubor prostředků, obsahovat směrnice času kompilace (například ty, které podmíněně zahrnout prostředky), nebo obsahují prostředky ve vlastním formátu. Můžete také použít **pole direktivy kompilace** mají zahrnout soubory prostředků standardní knihovny MFC. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

> [!NOTE]
> Zobrazí položky v těchto textových polí v souboru .rc, které jsou označené nástrojem `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, a `TEXTINCLUDE 3` v uvedeném pořadí. Další informace najdete v tématu [TN035: použití více zdrojových souborů a soubory hlaviček s jazykem Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Jakmile se změny provedené pomocí souboru prostředků **prostředek zahrnuje** dialogové okno, budete muset zavřít soubor .rc a znovu ho, aby se změny projevily. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Určení adresářů souborů k zahrnutí pro prostředky](../windows/how-to-specify-include-directories-for-resources.md)<br/>
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)