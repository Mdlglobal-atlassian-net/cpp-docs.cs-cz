---
title: Používání operátorů v blocích __asm
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: a871c19942252bf6a1a4901f8854b7b759700cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166500"
---
# <a name="using-operators-in-asm-blocks"></a>Používání operátorů v blocích __asm

**Microsoft Specific**

`__asm` Block nemůže používat konkrétní operátory jazyka C nebo C++, jako **<<** operátor. Ale operátory sdílí C a MASM, například \* operátoru, jsou interpretovány jako operátory jazyka sestavení. Například mimo `__asm` blokovat, hranaté závorky (**[] č.**) jsou interpretovány jako vnější subscripty pole, které C automaticky škáluje, aby velikost prvku v poli. Uvnitř `__asm` bloku, že se zobrazují jako MASM operátoru indexu, který dává za bajtovým posunem. z jakéhokoli datového objektu nebo popisek (ne jenom pole). Následující kód ukazuje rozdíl:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

První odkaz na `array` nezmění, ale druhá. Všimněte si, že můžete použít **typ** operátor k dosažení škálování podle konstantu. Například následující příkazy jsou ekvivalentní:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>