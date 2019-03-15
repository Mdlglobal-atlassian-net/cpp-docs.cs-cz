---
title: Soubory definice modulu (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812236"
---
# <a name="module-definition-def-files"></a>Soubory definice modulu (.Def)

Soubory definice modulu (.def) poskytují linkeru s informacemi o vývozu, atributy a jiné informace o programu, který chcete propojit. Soubor .def je nejužitečnější při sestavování knihovny DLL. Protože jsou [možnosti Linkeru MSVC](linker-options.md) , který lze použít místo příkazy definice modulu .def soubory nejsou obecně nezbytné. Můžete také použít [__declspec(dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md) jako způsob, jak určit exportované funkce.

Soubor .def můžete vyvolat během fáze linkeru s [def (zadat soubor definice modulu)](def-specify-module-definition-file.md) – možnost linkeru.

Pokud sestavujete soubor .exe, který nemá žádné exporty, pomocí souboru .def budou načítání vaše výstupní soubor pomalejší a větší.

Příklad najdete v tématu [export z knihovny DLL pomocí souborů DEF](../exporting-from-a-dll-using-def-files.md).

Najdete v následujících částech Další informace:

- [Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)

- [EXPORTY](exports.md)

- [VELIKOST HALDY](heapsize.md)

- [KNIHOVNA](library.md)

- [JMÉNO](name-c-cpp.md)

- [ODDÍLY](sections-c-cpp.md)

- [VELIKOST ZÁSOBNÍKU](stacksize.md)

- [ZÁSTUPNÁ PROCEDURA](stub.md)

- [VERZE](version-c-cpp.md)

- [Vyhrazená slova](reserved-words.md)

## <a name="see-also"></a>Viz také:

[Referenční zdroje k sestavení programu v jazyce C/C++](c-cpp-building-reference.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
