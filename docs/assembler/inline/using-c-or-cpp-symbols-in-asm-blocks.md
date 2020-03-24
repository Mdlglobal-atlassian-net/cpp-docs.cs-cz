---
title: Používání symbolů jazyka C nebo C++ v blocích __asm
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: fd9f8b444d263818aca1b16260f70730d5350e7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169107"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Používání symbolů jazyka C nebo C++ v blocích __asm

**Specifické pro společnost Microsoft**

`__asm` blok může odkazovat na libovolný C nebo C++ symbol v oboru, kde se objeví blok. (Symboly jazyka C++ C a jsou názvy proměnných, názvy funkcí a popisky; to znamená názvy, které nejsou symbolické konstanty nebo `enum` členy. Nemůžete C++ volat členské funkce.)

Pro použití značek C a C++ se platí několik omezení:

- Každý příkaz Assembly-Language může obsahovat pouze jeden znak C C++ nebo symbol. Ve stejné instrukci sestavení se může zobrazit více symbolů pouze s výrazy **Length**, **Type**a **Size** .

- Funkce, na které se odkazuje v bloku `__asm`, musí být v programu deklarovány (prototyped) dříve. V opačném případě kompilátor nemůže rozlišovat mezi názvy a popisky funkcí v bloku `__asm`.

- Blok `__asm` nemůže použít žádné symboly jazyka C C++ nebo, které mají stejnou pravopis, jako MASM vyhrazená slova (bez ohledu na velikost písmen). MASM vyhrazená slova zahrnují názvy instrukcí, jako **jsou například zápis a zápis** názvů, jako je například si.

- Značky struktury a sjednocení nejsou v blocích `__asm` rozpoznány.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
