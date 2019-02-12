---
title: Souhrn příkazů
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 76a549de7791f8af36fbf150c19cf6ed0de2cbe6
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152752"
---
# <a name="summary-of-statements"></a>Souhrn příkazů

*příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz s popiskem*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*compound-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz výrazu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz výběru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iterace – příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz-skoku*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s výjimkou příkazu Try*  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-statement*  / \* specifické pro Microsoft \*/

*příkaz-skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**příkaz goto***identifikátor***;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pokračování**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Konec;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Vrátí** *výraz*<sub>optimalizované</sub> **;**

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *seznam deklarací*<sub>optimalizované</sub> *seznamu příkazů*<sub>optimalizované</sub> **}**

*seznam deklarací*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam deklarací* *deklarace*

*seznam příkazů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam příkazů* *– příkaz*

*příkaz výrazu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz*<sub>optimalizované</sub> **;**

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zatímco (**  *výraz*  **)**  *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**proveďte***příkaz***během (***výraz***);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pro (***výraz*<sub>optimalizované</sub> **;** *výraz*<sub>optimalizované</sub> **;** *výraz*<sub>optimalizované</sub> **)** *– příkaz*

*příkaz výběru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Pokud (***výraz***)***– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Pokud (***výraz***)***příkaz***else***– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Přepnout (***výraz***)***– příkaz*

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor***:***– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**případ**  *konstantní výraz*  **:**  *– příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Výchozí:**  *– příkaz*

*s výjimkou příkazu Try*: /\* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try***compound-statement* **__except (***výraz***)***compound-statement* 

*try-finally-statement*: /\* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try***compound-statement* **__finally***compound-statement* 

## <a name="see-also"></a>Viz také:

[Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)
