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
&nbsp;&nbsp;&nbsp;&nbsp;*složený příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz Expression-*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Výběr – příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz iterace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz skoku*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except – příkaz*  / \* Specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-– příkaz*  / \* Specifické pro společnost Microsoft\*/

*příkaz skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *identifikátor*  **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pokraeovat**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**rozdělován**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**návratový** *výraz*<sub>opt</sub> **;**

*složený příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklarace-seznam*příkazů<sub>opt</sub> *-list*<sub>opt</sub> **}**

*seznam deklarací*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*změny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *seznamu deklarací* *declaration*

*seznam příkazů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*vydá*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;příkaz *-list –* *příkaz*

*příkaz Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz*<sub>opt</sub> **;**

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while**–*příkaz* (*Expression***)**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**do**  *– příkaz*  **while (**  *výraz*  **);**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pro (**  *výraz*<sub>opt</sub> **;** *Expression*<sub>opt</sub> **;** *výraz*<sub>opt</sub> **)** – *příkaz*

*příkaz výběru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if**–*příkaz* (*Expression***)**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if**–*příkaz* *výrazu***)***statement***Else**          <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Switch**–*příkaz* (*výraz***)**      

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*  **: –**  *příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**case**  *konstanta-výraz*  **:**  *příkaz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Default: –**  *příkaz*

*try-except – příkaz*:/ \* specifické pro Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz* **__try**složeného*příkazu* **__except (***Expression***)**        

*try-finally-příkaz*:/ \* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**  *složený* příkaz **__finally**  *složeného příkazu*

## <a name="see-also"></a>Viz také

[Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)
