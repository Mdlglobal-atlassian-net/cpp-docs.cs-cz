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

"Textový literál" je posloupnost znaků ze zdrojové znakové sady uzavřený do dvojitých uvozovek ( **""** ). Řetězcové literály se používají k vyjádření posloupnost znaků, které, dohromady, tvoří řetězec zakončený hodnotou null. Musíte vždy přidat předponu literály širokých řetězců s písmenem **L**.

## <a name="syntax"></a>Syntaxe

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **"** *s – znak sekvence*<sub>optimalizované</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s – znak sekvence*<sub>optimalizované</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s – znak sekvence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Každý člen zdrojové znakové sady kromě dvojité uvozovky ("), zpětného lomítka (\\), nebo znak nového řádku

&nbsp;&nbsp;&nbsp;&nbsp;*řídicí sekvence*

## <a name="remarks"></a>Poznámky

Následující příklad je jednoduchý řetězcový literál:

```C
char *amessage = "This is a string literal.";
```

Všechny kódy řídicí [řídicí sekvence](../c-language/escape-sequences.md) tabulky jsou platné u řetězcových literálů. K reprezentaci dvojité uvozovky v řetězcovém literálu, použijte sekvenci escape  **\\"** . Jednoduché uvozovky ( **"** ) můžou být vyjádřeny bez řídicí sekvence. Zpětné lomítko ( **\\** ) musí být následován se druhé zpětné lomítko ( **\\\\** ) Pokud je zobrazeno v rámci řetězce. Když se objeví zpětné lomítko na konci řádku, je vždy interpretován jako znak pro pokračování řádku.

## <a name="see-also"></a>Viz také:

[Elementy jazyka C](../c-language/elements-of-c.md)
