---
title: Přechod na popisky v sestavení inline assemblerem
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 199156a08af13f4a70793609b37c70b0c95bf9ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169328"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Přechod na popisky v sestavení inline assemblerem

**Specifické pro společnost Microsoft**

Podobně jako běžné označení C C++ nebo Label má popisek v `__asm` bloku rozsah celé funkce, ve které je definován (nikoli pouze v bloku). Příkazy sestavení i příkazy `goto` mohou přejít na popisky uvnitř nebo vně bloku `__asm`.

Popisky definované v blocích `__asm` nerozlišují velká a malá písmena. příkazy `goto` a pokyny k sestavení mohou na tyto štítky odkazovat bez ohledu na velikost písmen. Popisky C C++ a rozlišují velká a malá písmena, pokud jsou používány příkazy `goto`. Pokyny k sestavení mohou přejít na označení C C++ nebo Label bez ohledu na velikost písmen.

Následující kód ukazuje všechny permutace:

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

Nepoužívejte názvy funkcí knihoven jazyka C jako popisky v `__asm`ch blocích. Můžete například zvážit použití `exit` jako popisku následujícím způsobem:

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Vzhledem k tomu, že funkce **Exit** je názvem funkce knihovny jazyka C, může tento kód způsobit skok na funkci **Exit** místo do požadovaného umístění.

Jako v programech MASM program symbol dolaru (`$`) slouží jako čítač aktuálního umístění. Je to popisek pro instrukci, která se právě sestavuje. V `__asm`ch blocích je hlavním využitím udělat dlouhý podmíněný skok:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
