---
title: .PUSHFRAME
description: Popisuje. PUSHFRAME MASM – direktiva slouží k určení, jak se má převinout funkce rámce.
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 5f951396291ecb12dab500a364f176106c5daa8b
ms.sourcegitcommit: 2cac0150ab3bc8260f866451019b8e22c7e1ac11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945849"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje položku ne`UWOP_PUSH_MACHFRAME`ho kódu unwind. Pokud je zadáno volitelné klíčové slovo **kódu** , je položka unwind kódu předána modifikátoru 1. V opačném případě je modifikátor 0.

## <a name="syntax"></a>Syntaxe

> **. PUSHFRAME** ⟦**Code**⟧;;

## <a name="remarks"></a>Poznámky

. PUSHFRAME umožňuje uživatelům ml64. exe určit, jak se funkce rámce odvíjí. Je povolená jenom v rámci prologu, který rozšiřuje z deklarace snímku [proc](../../assembler/masm/proc.md) na [. ](../../assembler/masm/dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. PUSHFRAME** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je dobrým zvykem zabalit jak direktivy unwind, tak kód, který jsou určeny k tomu, aby se zajistila shoda v makru.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
