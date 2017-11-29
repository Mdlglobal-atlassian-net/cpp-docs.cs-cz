---
title: "Přechod na popisky ve vloženém sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3cec845e83e41f71496d1384396e7dd370dc0406
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Přechod na popisky v sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Jako obyčejnou jazyka C nebo C++ popisek, název v `__asm` bloku má obor v rámci funkce, ve kterém je definovaný (ne jenom v bloku). Obě sestavení pokyny a `goto` příkazy můžete přejít na popisky uvnitř nebo vně `__asm` bloku.  
  
 Popisky definované ve `__asm` bloky nejsou velká a malá písmena; obě `goto` příkazy a pokyny sestavení může odkazovat na tyto popisky bez ohledu na případ. Jazyk C a C++ popisky jsou velká a malá písmena pouze při použití `goto` příkazy. Pokyny k sestavení můžete přejít k jazyka C nebo C++ popisek bez ohledu na případ.  
  
 Následující kód ukazuje všechny permutací:  
  
```  
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
  
 Nepoužívejte názvy funkce knihoven C jako popisky v `__asm` bloky. Například může být rozhodnout použít `exit` jako popisek, následujícím způsobem:  
  
```  
; BAD TECHNIQUE: using library function name as label  
jne exit  
   .  
   .  
   .  
exit:  
   ; More __asm code follows  
```  
  
 Protože **ukončete** je název funkce C knihovny, tento kód může způsobit přechod na **ukončete** funkce místo do požadovaného umístění.  
  
 Jako MASM programy, symbol dolaru (`$`) slouží jako čítač aktuální umístění. Popisek pro pokyn aktuálně připojení, přičemž je. V `__asm` bloky, nejčastěji se využívá spočívá v učinění dlouho podmíněného přeskakování:  
  
```  
jne $+5 ; next instruction is 5 bytes long  
jmp farlabel  
; $+5  
   .  
   .  
   .  
farlabel:  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vložený Assembler](../../assembler/inline/inline-assembler.md)