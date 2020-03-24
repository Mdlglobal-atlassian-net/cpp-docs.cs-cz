---
title: Přehled inline assembleru
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 6233e07e115c21a0a173f094079dc9c1753533b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169394"
---
# <a name="inline-assembler-overview"></a>Přehled inline assembleru

**Specifické pro společnost Microsoft**

Inline assembler umožňuje vložit instrukce pro sestavení jazyka v jazyce C a C++ zdrojové programy bez dalších kroků sestavení a propojení. Vložený assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).

Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Kód vloženého sestavení může používat libovolný název C++ jazyka c nebo proměnné nebo funkce, který je v oboru, takže jej lze snadno integrovat s kódem jazyka c C++ a programem. A vzhledem k tomu, že kód sestavení lze kombinovat s C++ příkazy jazyka c a, může provádět úkoly, které jsou náročné nebo nemožné C++ v c nebo samostatně.

Klíčové slovo [__asm](../../assembler/inline/asm.md) vyvolá vložený assembler a může se objevit všude, kde je výraz C++ C nebo platný. Nemůže být použit sám sebou. Musí následovat instrukce sestavení, skupina instrukcí uzavřených ve složených závorkách nebo, minimálně prázdný pár složených závorek. Termín "`__asm` blok" tady odkazuje na jakoukoli instrukci nebo skupinu instrukcí, bez ohledu na to, jestli jsou ve složených závorkách.

Následující kód je jednoduchý `__asm` blok uzavřený ve složených závorkách. (Kód je posloupnost vlastní funkce sekvence prologu.)

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
