---
title: Přehled inline assembleru
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 21e0d9ca0e64922b83518eb79c19d2f2e67813bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167008"
---
# <a name="inline-assembler-overview"></a>Přehled inline assembleru

**Microsoft Specific**

Vložený assembler umožňuje vložení instrukcí sestavení jazyka ve svých programech zdroj C a C++ bez nutnosti dodatečných kroků sestavení a propojení. Vložený assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).

Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Vložený kód sestavení můžete použít libovolný jazyka C nebo C++ název proměnné nebo funkce, která je v oboru, takže můžete snadno ji integrovat s kódu vašeho programu jazyka C a C++. A protože lze kód sestavení kombinovat s příkazy jazyka C a C++, lze provádět úkoly, které jsou náročné nebo nemožné v jazyce C nebo C++ samostatně.

[__Asm](../../assembler/inline/asm.md) – klíčové slovo vyvolá vložený assembler a může vyskytovat kdekoli a C nebo C++ příkaz. Se nemůže objevit samostatně. Musí následovat instrukce sestavení, skupina pokynů uzavřená v závorkách, nebo přinejmenším, prázdný pár závorek. Termín "`__asm` blok" zde vztahuje na jakoukoli instrukci nebo skupinu instrukcí ve složených závorkách, zda je či není.

Následující kód je jednoduchý `__asm` bloku, které jsou uzavřeny ve složených závorkách. (Kód je posloupnost vlastní funkce sekvence prologu.)

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

Alternativně můžete umístit `__asm` před každou instrukci sestavení:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Protože klíčové slovo `__asm` představuje oddělovač výrazů, lze také umístit pokyny sestavení na stejný řádek:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>