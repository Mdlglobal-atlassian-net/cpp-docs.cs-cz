---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 9ea506e25435c5d6f1b10eab8c4f25f72bf88791
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178433"
---
# <a name="pushframe"></a>.PUSHFRAME

Generuje `UWOP_PUSH_MACHFRAME` unwind položky kódu. Pokud volitelný `code` je zadán kód položka unwind dostane Modifikátor 1. V opačném případě Modifikátor je 0.

## <a name="syntax"></a>Syntaxe

> . PUSHFRAME [kód]

## <a name="remarks"></a>Poznámky

. PUSHFRAME umožňuje uživatelům ml64.exe k určení, jak funkce rámce unwinds a je povolený jenom v rámci prologu, který se táhne od [PROC](../../assembler/masm/proc.md) prohlášení rámce [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) směrnice. Tyto direktivy negeneruje kód; pouze generovat `.xdata` a `.pdata`. . PUSHFRAME by měl předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. To je dobrý postup při zabalení direktivy unwind a kódu, které jsou určeny k unwind v makru zajistit smlouvy.

Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>