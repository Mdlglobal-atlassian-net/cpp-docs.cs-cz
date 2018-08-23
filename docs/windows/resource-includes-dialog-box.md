---
title: Prostředek zahrnuje – dialogové | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourceincludes
dev_langs:
- C++
helpviewer_keywords:
- Resource Includes dialog box
- rc files, changing storage
- symbol header files, changing
- compiling source code, including resources
- .rc files, changing storage
- symbol header files, read-only
- symbols, symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96ee92f1b21d67321b95a169cbc4c47eaca2de17
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610658"
---
# <a name="resource-includes-dialog-box"></a>Dialogové okno Prostředek zahrnuje

Můžete použít **prostředek zahrnuje** dialogové okno Upravit prostředí normální funkční uspořádání ukládání všech prostředků v projektu soubor .rc a všechny [symboly](../windows/symbols-resource-identifiers.md) v souboru Resource.h.

Chcete-li otevřít **prostředek zahrnuje** dialogové okno, klikněte pravým tlačítkem na příslušný .rc souborů v [zobrazení prostředků](../windows/resource-view-window.md), klikněte na tlačítko **prostředek zahrnuje** z místní nabídky.

**Hlavičkový soubor symbolů**  
Umožňuje změnit název hlavičkového souboru, kde jsou uloženy definice symbolů pro váš soubor prostředků. Další informace najdete v tématu [mění se názvy z hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md).

**Směrnice souborů jen pro čtení**  
Umožňuje zahrnout soubory hlaviček, které obsahují symboly, které by se nemělo upravovat během úprav relace. Například můžete zahrnout soubor se symboly, jež jsou sdílena mezi několika projekty. Můžete také zahrnout soubory hlaviček knihovny MFC. Další informace najdete v tématu [zahrnutí sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md).

**Směrnice času kompilace**  
Umožňuje zahrnout soubory prostředků, které vytvářejí se a upravují samostatně z prostředků v hlavní soubor prostředků, obsahovat směrnice času kompilace (například ty, které podmíněně zahrnout prostředky), nebo obsahují prostředky ve vlastním formátu. Můžete také použít **pole direktivy kompilace** mají zahrnout soubory prostředků standardní knihovny MFC. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

> [!NOTE]
> Zobrazí položky v těchto textových polí v souboru .rc, které jsou označené nástrojem `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, a `TEXTINCLUDE 3` v uvedeném pořadí. Další informace najdete v tématu [TN035: použití více zdrojových souborů a soubory hlaviček s jazykem Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Jakmile se změny provedené pomocí souboru prostředků **prostředek zahrnuje** dialogové okno, budete muset zavřít soubor .rc a znovu ho, aby se změny projevily. Další informace najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Určení adresářů souborů k zahrnutí pro prostředky](../windows/how-to-specify-include-directories-for-resources.md)  
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)