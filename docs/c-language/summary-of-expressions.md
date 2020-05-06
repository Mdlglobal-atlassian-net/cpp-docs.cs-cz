---
title: Souhrn výrazů
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 320baa51d54f00ac4fdb6633922a8bb36cf92a94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157815"
---
# <a name="summary-of-expressions"></a>Souhrn výrazů

*primární výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*změnil*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*řetězcový literál*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *výraz*  **)**

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz*  **,**  *přiřazení – výraz*

*konstantní výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*podmíněný výraz*

*podmíněný výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz or*  **?**  *výraz*  **:**  *podmíněný výraz*

*výraz přiřazení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*podmíněný výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;přiřazení *unárního výrazu* – *výraz přiřazení* *operátoru*

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příponový výraz*  **[**  *výraz*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***.**    *RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor výrazu přípony***->***identifier*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list*  **,**  *přiřazení-výraz*

*unární výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární – operátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof**  *unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *název typu*  **)**

*unární – operátor*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&****&#42;** **+**&#42;**-** **!** ! **~**

*výraz cast*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *název typu*  **)**  *přetypování – výraz*

*multiplikativní-výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní-expression* **&#42;** *cast-expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní –***/***výraz cast-* Expression    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní –***%***výraz cast-* Expression    

*výraz doplňkového výrazu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz doplňkového výrazu*  **+**  *multiplikativní-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz doplňkového výrazu*  **-**  *multiplikativní-Expression*

*SHIFT-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz doplňkového výrazu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression***\<***výraz doplňkového* výrazu Shift-Expression    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression***>>***výraz doplňkového* výrazu Shift-Expression    

*relační výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Shift-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***\<**–*SHIFT-Expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***>**–*SHIFT-Expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***\<**–*SHIFT-Expression*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz***>=**–*SHIFT-Expression*    

*výraz rovnosti*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz rovnosti*–*výraz* **==**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rovnost-Expression*  **! =**  *relační výraz*

*A-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*Výraz rovnosti a výrazu*equality-expression* **&**    

*výhradní nebo výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*A – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výhradní výraz***^** or*a-Expression*    

*výraz (včetně)*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výhradní nebo výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz* **&#124;** *Exclusive* nebo-Expression    

*logický operátor and-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz (včetně)*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz logického operátoru and a Expression*  **&&**  *(včetně)*

*logický výraz or*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický operátor AND-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;logický operátor *OR* **&#124;&#124;** *logický operátor and-Expression*    

## <a name="see-also"></a>Viz také

- [Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)
