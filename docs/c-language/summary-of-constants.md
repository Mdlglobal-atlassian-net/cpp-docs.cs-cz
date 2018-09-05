---
title: Souhrn konstant | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33367c468d8e499382c30642dd55c4cd7fd1a59a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760491"
---
# <a name="summary-of-constants"></a>Souhrn konstant

*konstantní*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*plovoucí desetinnou – konstanta*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta typu Integer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Znaková konstanta*

*konstanta plovoucí desetinnou*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *exponent část*<sub>optimalizované</sub> *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *exponent část* *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub>

*desetinná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*<sub>optimalizované</sub> **.** *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic***.**

*exponent část*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**elektronické** *přihlašování*<sub>optimalizované</sub> *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**elektronické** *přihlašování*<sub>optimalizované</sub> *sekvence číslic*

*znaménko*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekvence číslic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *číslice*

*číslo s plovoucí čárkou přípona*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l f F L**

*celočíselná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *číselnou příponou*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*binární soubor konstanta* *číselnou příponou*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičkové konstanty* *číselnou příponou*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*šestnáctkové konstanty* *číselnou příponou*<sub>optimalizované</sub>

*desetinná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenulovou číslicí.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *číslice*

*binární soubor konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *binární číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *binární číslice*

*osmičkové konstanty*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičkové konstanty* *uveden jako osmičková číslice*

*šestnáctkové konstanty*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 x***šestnáctkové číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 X***šestnáctkové číslice* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*šestnáctkové konstanty* *šestnáctkové číslice*

*nenulovou číslicí*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*uveden jako osmičková číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*šestnáctkové číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*unsigned-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*Long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*Znaková konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *c-char pořadí* **.**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L "** *c-char pořadí* **.**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long-suffix* *unsigned-suffix*<sub>optimalizované</sub>

*c – znak sekvence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c – znak sekvence* *c-char*

*c – znak*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Každý člen zdrojové znakové sady kromě jednoduché uvozovky (**"**), zpětného lomítka (**\\**), nebo sekvence escape znaků nového řádku

*řídicí sekvence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Simple-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičková řídicí sekvence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*šestnáctková řídicí sekvence*

*Simple-escape-sequence*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b \f \n \r \t \V**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*osmičková řídicí sekvence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *uveden jako osmičková číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *uveden jako osmičková číslice* *uveden jako osmičková číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *uveden jako osmičková číslice* *uveden jako osmičková číslice* *uveden jako osmičková číslice*

*šestnáctková řídicí sekvence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *šestnáctkové číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*šestnáctková řídicí sekvence* *šestnáctkové číslice*

## <a name="see-also"></a>Viz také

[Gramatika slov](../c-language/lexical-grammar.md)<br/>
