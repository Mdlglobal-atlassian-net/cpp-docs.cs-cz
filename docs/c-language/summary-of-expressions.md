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

*primary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanty*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*řetězcový literál*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *výraz* **)**

*výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz* **,** *výrazu přiřazení*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR* **?**  *výraz* **:** *podmíněného výrazu*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **[**  *výraz*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>optimalizované</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **->**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *výrazu přiřazení*

*unary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **++**  *Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **--**  *Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz CAST*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**operátor sizeof:** *unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (** *název typu* **)**

*Unární operátor*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **&** **&#42;** **+** **-** **~** **!**

*výraz CAST*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *název typu*  **)**  *výrazem přetypování.*

*multiplicative-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz CAST*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz* **&#42;** *výrazem přetypování.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz* **/** *výrazem přetypování.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz* **%** *výrazem přetypování.*

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplikativní výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*  **+**  *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*  **-**  *multiplicative-expression*

*shift-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*  **\<\<**  *additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*SHIFT-expression* **>>** *additive-expression*

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **\<** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **>** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **\<=** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **>=** *shift-expression*

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti* **==** *relační výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti* **! =** *relační výraz*

*A výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz rovnosti*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Výraz AND* **&** *výrazu rovnosti*

*exclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Výraz AND*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz exkluzivní OR* **^** *výraz AND*

*inclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz exkluzivní OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inkluzivní výraz OR* **&#124;** *výraz exkluzivní OR*

*logical-AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inkluzivní nebo výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický a výraz* **&&** *včetně výraz OR*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický a výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR* **&#124;&#124;** *logické a expression*

## <a name="see-also"></a>Viz také:

- [Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)
