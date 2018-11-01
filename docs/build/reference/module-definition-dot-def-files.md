---
title: Soubory definice modulu (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: a882d71e76b961fefb7059bee8634507f12f7986
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460434"
---
# <a name="module-definition-def-files"></a>Soubory definice modulu (.Def)

Soubory definice modulu (.def) poskytují linkeru s informacemi o vývozu, atributy a jiné informace o programu, který chcete propojit. Soubor .def je nejužitečnější při sestavování knihovny DLL. Protože jsou [možnosti linkeru](../../build/reference/linker-options.md) , který lze použít místo příkazy definice modulu .def soubory nejsou obecně nezbytné. Můžete také použít [__declspec(dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) jako způsob, jak určit exportované funkce.

Soubor .def můžete vyvolat během fáze linkeru s [def (zadat soubor definice modulu)](../../build/reference/def-specify-module-definition-file.md) – možnost linkeru.

Pokud sestavujete soubor .exe, který nemá žádné exporty, pomocí souboru .def budou načítání vaše výstupní soubor pomalejší a větší.

Příklad najdete v tématu [export z knihovny DLL pomocí souborů DEF](../../build/exporting-from-a-dll-using-def-files.md).

Najdete v následujících částech Další informace:

- [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)

- [EXPORTY](../../build/reference/exports.md)

- [VELIKOST HALDY](../../build/reference/heapsize.md)

- [KNIHOVNA](../../build/reference/library.md)

- [JMÉNO](../../build/reference/name-c-cpp.md)

- [ODDÍLY](../../build/reference/sections-c-cpp.md)

- [VELIKOST ZÁSOBNÍKU](../../build/reference/stacksize.md)

- [ZÁSTUPNÁ PROCEDURA](../../build/reference/stub.md)

- [VERZE](../../build/reference/version-c-cpp.md)

- [Vyhrazená slova](../../build/reference/reserved-words.md)

## <a name="see-also"></a>Viz také

[Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)