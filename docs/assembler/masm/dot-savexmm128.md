---
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 6402b75c10b1400d56923116621f00b4d0908822
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318251"
---
# <a name="savexmm128"></a>.SAVEXMM128

Generuje položku `UWOP_SAVE_XMM128` nebo `UWOP_SAVE_XMM128_FAR` unwind kódu pro zadaný registr XMM a posun pomocí aktuálního posunu prologu. MASM bude zvolit nejúčinnější kódování.

## <a name="syntax"></a>Syntaxe

> **. SAVEXMM128** *xmmreg* , *posun*

## <a name="remarks"></a>Poznámky

**. SAVEXMM128** umožňuje uživatelům ml64. exe určit, jak se funkce rámce odvíjí, a je povoleno pouze v prologu, které se rozšíří z deklarace snímku [proc](proc.md) na [. ](dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. . SAVEXMM128 by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

*posun* musí být násobkem 16.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
