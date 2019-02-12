---
title: Souhrn konstant
ms.date: 11/04/2016
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
ms.openlocfilehash: f927d977d818bed28c5fd7392f7933cd1a63ced3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150022"
---
# <a name="summary-of-constants"></a>Souhrn konstant

*konstantní*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*floating-point-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*integer-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*character-constant*

*floating-point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *exponent část*<sub>optimalizované</sub> *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *exponent část* *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub>

*desetinná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*<sub>optimalizované</sub> **.** *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*  **.**

*exponent-part*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**elektronické** *přihlašování*<sub>optimalizované</sub> *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**elektronické** *přihlašování*<sub>optimalizované</sub> *sekvence číslic*

*znaménko*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekvence číslic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *číslice*

*číslo s plovoucí čárkou přípona*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l f F L**

*integer-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*binární soubor konstanta* *číselnou příponou*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*

*binární soubor konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *binary-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0B** *binary-digit*

*osmičkové konstanty*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0X**  *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*

*nenulovou číslicí*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*uveden jako osmičková číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*šestnáctkové číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*unsigned-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*Long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*character-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *c-char pořadí* **.**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L "** *c-char pořadí* **.**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long-suffix* *unsigned-suffix*<sub>optimalizované</sub>

*c-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c – znak sekvence* *c-char*

*c-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Každý člen zdrojové znakové sady kromě jednoduché uvozovky (**"**), zpětného lomítka (**\\**), nebo sekvence escape znaků nového řádku

*řídicí sekvence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*simple-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-escape-sequence*

*Simple-escape-sequence*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\a \b \f \n \r \t \V**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\' \\" \\\ \\?**

*osmičková řídicí sekvence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *uveden jako osmičková číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *octal-digit* *octal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\\** *octal-digit* *octal-digit* *octal-digit*

*hexadecimal-escape-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\x** *šestnáctkové číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-escape-sequence* *hexadecimal-digit*

## <a name="see-also"></a>Viz také:

[Gramatika slov](../c-language/lexical-grammar.md)<br/>
