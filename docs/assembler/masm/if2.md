---
title: IF1 a IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: f1b5126d9294c229d773acd29af463164bb46536
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397450"
---
# <a name="if1-and-if2"></a>IF1 a IF2

**IF1** blok se vyhodnocuje při prvním průchodu sestavení.

Blok **IF2** je vyhodnocen u všech průchodů sestavení, pokud je **parametr: SETIF2** **true**.

## <a name="syntax"></a>Syntaxe

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>Poznámky

Úplnou syntaxi naleznete v tématu [if](../../assembler/masm/if-masm.md) .

Na rozdíl od verze 5,1, MASM 6,1 a vyšší provádí většinu práce na prvním průchodu, pak provede libovolný počet následných průchodů podle potřeby. Naproti tomu MASM 5,1 vždy sestaví dva zdrojové průchody. V důsledku toho může být nutné upravit nebo odstranit některé konstrukty závislé na průchodech v MASM 6,1 a vyšších.

### <a name="two-pass-directives"></a>Direktivy dvojího předávání

Pro zajištění kompatibility MASM 6,1 a vyšší podporují direktivy 5,1, které odkazují na dva průchody. Patří mezi ně **. ERR1**, **. ERR2**, **IF1**, **IF2**, **ELSEIF1**a **ELSEIF2**. Pro druhé Pass konstrukce musíte zadat [možnost SETIF2](option-masm.md). Bez **Možnosti SETIF2**, **IF2** a **.** Direktivy Err2 způsobí chybu:

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6,1 a vyšší než rutina First – passuje jinak. Zpracovává se **.** Direktiva ERR1 jako **. ERR**a direktiva **IF1** jako **if**.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
