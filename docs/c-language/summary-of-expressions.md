---
title: Souhrn výrazů
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 320baa51d54f00ac4fdb6633922a8bb36cf92a94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543491"
---
# <a name="summary-of-expressions"></a>Souhrn výrazů

*primární výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanty*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*řetězcový literál*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(***výraz***)** 

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz***,***výrazu přiřazení* 

*konstantní výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Podmíněného výrazu*

*podmíněného výrazu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR***?**   *výraz***:***podmíněného výrazu*

*výraz přiřazení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Podmíněného výrazu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární výraz* *operátor přiřazení* *výrazu přiřazení*

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primární – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **[**  *výraz*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>optimalizované</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **.**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **->**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list***,***výrazu přiřazení* 

*Unární výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární operátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz CAST*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**operátor sizeof:***unární výraz* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (***název typu***)** 

*Unární operátor*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&** **&#42;****+** **-** **~** **!**

*výraz CAST*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *název typu*  **)**  *výrazem přetypování.*

*multiplikativní výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz CAST*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz***&#42;***výrazem přetypování.* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz***/***výrazem přetypování.* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz***%***výrazem přetypování.* 

*Additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression***+***násobení výraz* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression***-***násobení výraz* 

*SHIFT-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression***\<\<***additive-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression***>>***additive-expression* 

*relační výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***\<***shift-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***>***shift-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***\<=***shift-expression* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***>=***shift-expression* 

*výraz rovnosti*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti***==***relační výraz* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti***! =***relační výraz* 

*A výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Výraz AND***&***výrazu rovnosti* 

*výraz exkluzivní OR*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Výraz AND*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz exkluzivní OR***^***výraz AND* 

*Inkluzivní výraz OR*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz exkluzivní OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inkluzivní výraz OR***&#124;***výraz exkluzivní OR* 

*logický a výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inkluzivní nebo výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický a výraz***&&***včetně výraz OR* 

*logický výraz OR*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický a výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR***&#124;&#124;***logické a expression* 

## <a name="see-also"></a>Viz také:

- [Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)
