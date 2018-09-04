---
title: . PUSHFRAME | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .PUSHFRAME
dev_langs:
- C++
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c86ba043eb185e9cc5697f236b907ae8177d6824
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689486"
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