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
ms.openlocfilehash: 1b2ec146daf450c4302be9fea8fdd117ec6398da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167203"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Ladění a naslouchání vloženého sestavení

**Microsoft Specific**

Programy, který obsahuje vložený kód sestavení lze ladit pomocí ladicího programu úrovni zdroje, pokud kompilujete s [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost.

V rámci ladicího programu můžete nastavit zarážky v jazyce C nebo C++ a jazyk sestavení řádcích. Pokud povolíte smíšená sestavení a režim zdroje, můžete zobrazit zdroj a zpětně přeložený formu kódu sestavení.

Všimněte si, že umístění na jednom řádku více pokyny k sestavení nebo příkazy zdrojového jazyka může zabránit spuštění ladění. V režimu zdroje můžete nastavit zarážky na jednom řádku, ale nikoli na jednotlivé příkazy na stejném řádku ladicí program. Stejný princip platí pro `__asm` bloku definována jako C – makro rozbalí do jednoho logického řádku.

Pokud vytvoříte smíšené zdroje a výpis s sestavení [/FAS](../../build/reference/fa-fa-listing-file.md) – možnost kompilátoru, výpis obsahuje zdroje a sestavení formulářů každého řádku jazyka sestavení. Makra nejsou rozbalení ve výpisech, ale jsou rozbaleny během kompilace.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>