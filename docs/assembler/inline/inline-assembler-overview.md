---
title: Přehled inline assembleru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e52316a5080ce7d64d34a09aa265ea561c186ed
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681216"
---
# <a name="inline-assembler-overview"></a>Přehled inline assembleru

**Specifické pro Microsoft**

Vložený assembler umožňuje vložení instrukcí sestavení jazyka ve svých programech zdroj C a C++ bez nutnosti dodatečných kroků sestavení a propojení. Vložený assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).

Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Vložený kód sestavení můžete použít libovolný jazyka C nebo C++ název proměnné nebo funkce, která je v oboru, takže můžete snadno ji integrovat s kódu vašeho programu jazyka C a C++. A protože lze kód sestavení kombinovat s příkazy jazyka C a C++, lze provádět úkoly, které jsou náročné nebo nemožné v jazyce C nebo C++ samostatně.

[__Asm](../../assembler/inline/asm.md) – klíčové slovo vyvolá vložený assembler a může se objevit všude, kde je platný příkaz jazyka C nebo C++. Se nemůže objevit samostatně. Musí následovat instrukce sestavení, skupina pokynů uzavřená v závorkách, nebo přinejmenším, prázdný pár závorek. Termín "`__asm` blok" zde vztahuje na jakoukoli instrukci nebo skupinu instrukcí ve složených závorkách, zda je či není.

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