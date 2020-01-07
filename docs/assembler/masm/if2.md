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
ms.openlocfilehash: 60f8b0dcedb61ac06de929aff300845e342d7cfc
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317315"
---
# <a name="if1-and-if2"></a>IF1 a IF2

**IF1** blok se vyhodnocuje při prvním průchodu sestavení.

Blok **IF2** je vyhodnocen u všech průchodů sestavení, pokud je **parametr: SETIF2** **true**.

## <a name="syntax"></a>Syntaxe

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>Poznámky

Úplnou syntaxi naleznete v tématu [if](if-masm.md) .

Na rozdíl od verze 5,1, MASM 6,1 a vyšší provádí většinu práce na prvním průchodu, pak provede libovolný počet následných průchodů podle potřeby. Naproti tomu MASM 5,1 vždy sestaví dva zdrojové průchody. V důsledku toho může být nutné upravit nebo odstranit některé konstrukty závislé na průchodech v MASM 6,1 a vyšších.

### <a name="two-pass-directives"></a>Direktivy dvojího předávání

Pro zajištění kompatibility MASM 6,1 a vyšší podporují direktivy 5,1, které odkazují na dva průchody. Patří mezi ně **. ERR1**, **. ERR2**, **IF1**, **IF2**, **ELSEIF1**a **ELSEIF2**. Pro druhé Pass konstrukce musíte zadat [možnost SETIF2](option-masm.md). Bez **Možnosti SETIF2**, **IF2** a **.** Direktivy Err2 způsobí chybu:

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6,1 a vyšší než rutina First – passuje jinak. Zpracovává se **.** Direktiva ERR1 jako **. ERR**a direktiva **IF1** jako **if**.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
