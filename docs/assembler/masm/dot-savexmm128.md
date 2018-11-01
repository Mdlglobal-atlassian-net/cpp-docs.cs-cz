---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: c29ec47170c5e0f46f02d53f23ab477a79bbdc32
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507897"
---
# <a name="savexmm128"></a>.SAVEXMM128

Generuje buď `UWOP_SAVE_XMM128` nebo `UWOP_SAVE_XMM128_FAR` unwind položku kódu pro zadaný Registr XMM a posun pomocí aktuální posun prologu. MASM zvolí nejúčinnější kódování.

## <a name="syntax"></a>Syntaxe

> .savexmm128 xmmreg, posun

## <a name="remarks"></a>Poznámky

. SAVEXMM128 umožňuje uživatelům ml64.exe zadejte způsob, jakým funkce rámce unwinds se povoluje jenom v prologu, který se táhne od [PROC](../../assembler/masm/proc.md) prohlášení rámce [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) směrnice. Tyto direktivy negeneruje kód; pouze generovat `.xdata` a `.pdata`. . SAVEXMM128 by měl předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. To je dobrý postup při zabalení direktivy unwind a kódu, které jsou určeny k unwind v makru zajistit smlouvy.

*Posun* musí být násobkem 16.

Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>