---
title: Ladění a naslouchání vloženého sestavení
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 3254fb6b750466de0a38230c5e1cfa067c476f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169510"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Ladění a naslouchání vloženého sestavení

**Specifické pro společnost Microsoft**

Programy obsahující kód vloženého sestavení lze ladit pomocí ladicího programu na úrovni zdroje, pokud kompilujete pomocí možnosti [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

V rámci ladicího programu můžete nastavit zarážky na řádcích jazyka C C++ nebo i. Pokud povolíte smíšené sestavení a režim zdroje, můžete zobrazit zdrojovou i nepřeloženou formu kódu sestavení.

Všimněte si, že vložení několika instrukcí sestavení nebo příkazů zdrojového jazyka na jeden řádek může zabránit ladění. V režimu zdroje můžete použít ladicí program k nastavení zarážek na jednom řádku, ale ne na jednotlivých příkazech na stejném řádku. Stejný princip platí pro `__asm` blok definovaný jako makro jazyka C, které se rozšíří na jednu logickou čáru.

Vytvoříte-li smíšený seznam zdrojů a sestavení s možností kompilátoru [/FAS](../../build/reference/fa-fa-listing-file.md) , obsahuje seznam zdrojové i montážní formuláře každého sestavení-jazyka. Makra nejsou rozbalena v seznamech, ale během kompilace jsou rozbaleny.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
