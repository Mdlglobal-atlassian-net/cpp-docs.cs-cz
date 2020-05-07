---
title: Textové literály jazyka C
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: 0df7126efe5a5b2caa3a4fee51465d0dbe892e89
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400589"
---
# <a name="c-string-literals"></a>Textové literály jazyka C

"Řetězcový literál" je posloupnost znaků ze zdrojové znakové sady uzavřené v uvozovkách (**""**). Řetězcové literály slouží k reprezentaci posloupnosti znaků, které společně tvoří řetězec zakončený hodnotou null. Literály s velkým řetězcem je nutné vždy prefixovat s písmenem **L**.

## <a name="syntax"></a>Syntaxe

*řetězcový literál*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s-char-Sequence –*<sub>opt</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L "** *s-znak – opt-char-Sequence*<sub>opt</sub> **"**

*s-char-Sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s-char-Sequence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;libovolný člen zdrojové znakové sady s výjimkou dvojité uvozovky ("), zpětného lomítka\\() nebo znaku nového řádku.

&nbsp;&nbsp;&nbsp;&nbsp;*řídicí sekvence*

## <a name="remarks"></a>Poznámky

Níže uvedený příklad je jednoduchý řetězcový literál:

```C
char *amessage = "This is a string literal.";
```

Všechny řídicí kódy, které jsou uvedeny v tabulce [řídicích sekvencí](../c-language/escape-sequences.md) , jsou platné v řetězcových literálech. Chcete-li znázornit dvojitou uvozovku v řetězcovém literálu, použijte ** \\řídicí sekvenci**. Jednoduchá uvozovka (**'**) může být reprezentována bez řídicí sekvence. Po zpětném lomítku (**\\**) musí následovat druhé zpětné lomítko (**\\**), když se objeví v rámci řetězce. Když se na konci řádku objeví zpětné lomítko, je vždy interpretováno jako znak pro pokračování řádku.

## <a name="see-also"></a>Viz také

[Elementy jazyka C](../c-language/elements-of-c.md)
