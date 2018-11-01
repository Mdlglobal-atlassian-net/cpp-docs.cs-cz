---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: cac7aa7f2bdbf6b60831d2beb062f86559ec0358
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472815"
---
# <a name="savereg"></a>.SAVEREG

Generuje buď `UWOP_SAVE_NONVOL` nebo `UWOP_SAVE_NONVOL_FAR` unwind položku kódu pro zadaný registr (`reg`) a posun (`offset`) použitím aktuální posun prologu. MASM zvolí nejúčinnější kódování.

## <a name="syntax"></a>Syntaxe

> . Posun SAVEREG registru

## <a name="remarks"></a>Poznámky

. SAVEREG umožňuje uživatelům ml64.exe k určení, jak funkce rámce unwinds a je povolený jenom v rámci prologu, který se táhne od [PROC](../../assembler/masm/proc.md) prohlášení rámce [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) směrnice. Tyto direktivy negeneruje kód; pouze generovat `.xdata` a `.pdata`. . SAVEREG by měl předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. To je dobrý postup při zabalení direktivy unwind a kódu, které jsou určeny k unwind v makru zajistit smlouvy.

Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>