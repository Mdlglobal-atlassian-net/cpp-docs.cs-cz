---
title: Souhrn příkazů
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 1a230ca7d998316d2ec96e76b54ac60575acd2ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856992"
---
# <a name="summary-of-statements"></a>Souhrn příkazů

*příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz s popiskem*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*složený* příkaz<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz Expression-*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výběru – příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iterace – příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz skoku*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-statement* /\* \*pro konkrétní Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-statement* /\* \*specifický pro společnost Microsoft /

*příkaz skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**příkaz goto** *identifikátor* **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pokračovat;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Break;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**návratový** *výraz*<sub>opt</sub> **;**

*složený příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *Declaration-list*<sub>opt</sub> *Statement-list*<sub>opt</sub> **}**

*seznam deklarací*:<br/>
*deklarace* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;*deklarace* &nbsp;*deklarace seznamu*

*seznam příkazů*:<br/>
&nbsp;&nbsp;&nbsp;*příkaz* &nbsp;<br/>
&nbsp;&nbsp; *&nbsp;příkazu &nbsp;* *-list*

*příkaz Expression*:<br/>
&nbsp;&nbsp;&nbsp;*výraz*&nbsp;<sub>opt</sub> **;**

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zatímco (**  *výraz*  **)**  *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**do***příkazu*do **(** *výraz* **);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pro (** *výraz*<sub>optimalizované</sub> **;** *výraz*<sub>optimalizované</sub> **;** *výraz*<sub>optimalizované</sub> **)** *– příkaz*

*příkaz výběru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Pokud (** *výraz* **)** *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Pokud (** *výraz* **)** *příkaz* **else** *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Přepnout (** *výraz* **)** *– příkaz*

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* **:** *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**případ**  *konstantní výraz*  **:**  *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Výchozí:**  *– příkaz*

*try-except – příkaz*:/\* \*specifický pro Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__except (** *výraz* **)** *compound-statement*

*try-finally-příkaz*:/\* \*specifický pro Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__finally** *compound-statement*

## <a name="see-also"></a>Viz také:

[Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)
