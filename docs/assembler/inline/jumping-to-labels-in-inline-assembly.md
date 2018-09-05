---
title: Přechod na popisky ve vloženém sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e697df32218c3e2bcdeb03cde44b7b5d854cb7b0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693621"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Přechod na popisky v sestavení inline assemblerem

**Specifické pro Microsoft**

Běžné jazyka C nebo C++ popisek, popisek v, jako jsou `__asm` bloku rozsahem v rámci funkce, ve kterém je definována (nikoli pouze v bloku). Obě pokyny k sestavení a `goto` příkazy Přejít na popisky uvnitř nebo vně `__asm` bloku.

Návěští definovaná ve `__asm` bloků nejsou malá a velká písmena; obě `goto` prohlášení a pokyny k sestavení mohou odkazovat na tyto popisky bez ohledu na případ. Popisky C a C++ jsou malá a velká písmena pouze při použití `goto` příkazy. Pokyny k sestavení můžete přejít na popisek jazyka C nebo C++ bez ohledu na případ.

Následující kód ukazuje všechny permutací:

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

Nepoužívejte názvy funkce knihovny C jako popisky v `__asm` bloky. Například můžete mít tendenci používat `exit` jako popisek, následujícím způsobem:

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Protože **ukončit** je název funkce knihovny C, tento kód může způsobit přechod **ukončit** místo funkce do požadovaného umístění.

Stejně jako v MASM programy, bude symbol dolaru (`$`) slouží jako aktuální umístění čítače. Popisek pro instrukci aktuálně připojení, přičemž je. V `__asm` bloky, nejčastěji je, aby dlouho podmíněné přeskakování:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>