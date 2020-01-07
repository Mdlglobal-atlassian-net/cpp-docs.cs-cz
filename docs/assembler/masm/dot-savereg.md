---
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 18cb6e563084e8c5357bec2a8052a2b38fcdffee
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317549"
---
# <a name="savereg"></a>.SAVEREG

Generuje položku `UWOP_SAVE_NONVOL` nebo `UWOP_SAVE_NONVOL_FAR` unwind kódu pro zadaný registr (*reg*) a posun (*posun*) pomocí aktuálního posunu prologu. MASM bude zvolit nejúčinnější kódování.

## <a name="syntax"></a>Syntaxe

> **. SAVEREG** *reg* __,__ *offset*

## <a name="remarks"></a>Poznámky

**. SAVEREG** umožňuje uživatelům ml64. exe určit způsob, jakým funkce rámce odvíjí a je povolena pouze v prologu, které se rozšíří z deklarace snímku [proc](proc.md) na [. ](dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. SAVEREG** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
