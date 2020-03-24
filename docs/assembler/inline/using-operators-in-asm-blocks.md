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
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169094"
---
# <a name="using-operators-in-__asm-blocks"></a>Používání operátorů v blocích __asm

**Specifické pro společnost Microsoft**

Blok `__asm` nemůže používat operátory jazyka C C++ nebo specifického typu, jako je například operátor **<<** . Nicméně operátory sdílené pomocí jazyka C a MASM, jako je například operátor \*, jsou interpretovány jako operátory pro sestavení jazyka. Například mimo blok `__asm`, jsou hranaté závorky ( **[]** ) interpretovány jako ohraničující podindexy pole, které jazyk C automaticky škáluje na velikost prvku v poli. Uvnitř bloku `__asm` se zobrazují jako operátor indexu MASM, který vydává posun bajt bez měřítka z libovolného datového objektu nebo popisku (nikoli pouze pole). Rozdíl je znázorněn v následujícím kódu:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

První odkaz na `array` není škálovaná, ale druhým je. Všimněte si, že operátor **Type** můžete použít k dosažení škálování na základě konstanty. Například následující příkazy jsou ekvivalentní:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
