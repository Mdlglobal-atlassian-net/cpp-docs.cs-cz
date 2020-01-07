---
title: .PUSHFRAME
description: Popisuje. PUSHFRAME MASM – direktiva slouží k určení, jak se má převinout funkce rámce.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 0aaec119d26d87fddb1eba505458da1250a5926e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317575"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje položku ne`UWOP_PUSH_MACHFRAME`ho kódu unwind. Pokud je zadáno volitelné klíčové slovo **kódu** , je položka unwind kódu předána modifikátoru 1. V opačném případě je modifikátor 0.

## <a name="syntax"></a>Syntaxe

> **. PUSHFRAME** ⟦**Code**⟧;;

## <a name="remarks"></a>Poznámky

. PUSHFRAME umožňuje uživatelům ml64. exe určit, jak se funkce rámce odvíjí. Je povolená jenom v rámci prologu, který rozšiřuje z deklarace snímku [proc](proc.md) na [. ](dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. PUSHFRAME** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je dobrým zvykem zabalit jak direktivy unwind, tak kód, který jsou určeny k tomu, aby se zajistila shoda v makru.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
