---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: b0f047278f6250d5ef359f7992df4ea23f4bbd9b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398048"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje položku ne`UWOP_PUSH_MACHFRAME`ho kódu unwind. Pokud je zadán volitelný *kód* , je položka unwind kódu dána modifikátorem 1. V opačném případě je modifikátor 0.

## <a name="syntax"></a>Syntaxe

> **. PUSHFRAME** ⟦*Code*⟧;;

## <a name="remarks"></a>Poznámky

. PUSHFRAME umožňuje uživatelům ml64. exe určit způsob, jakým funkce rámce odvíjí a je povolena pouze v prologu, které se rozšíří z deklarace snímku [proc](../../assembler/masm/proc.md) na [. ](../../assembler/masm/dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. PUSHFRAME** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
