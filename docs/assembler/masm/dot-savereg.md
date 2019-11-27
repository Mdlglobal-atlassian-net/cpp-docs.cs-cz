---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 324cf0e70a7ad619e5741c9acc18c24a72f54d13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397968"
---
# <a name="savereg"></a>.SAVEREG

Generuje položku `UWOP_SAVE_NONVOL` nebo `UWOP_SAVE_NONVOL_FAR` unwind kódu pro zadaný registr (*reg*) a posun (*posun*) pomocí aktuálního posunu prologu. MASM bude zvolit nejúčinnější kódování.

## <a name="syntax"></a>Syntaxe

> **. SAVEREG** *reg* __,__ *offset*

## <a name="remarks"></a>Poznámky

**. SAVEREG**umožňuje uživatelům ml64. exe určit způsob, jakým funkce rámce odvíjí a je povolena pouze v prologu, které se rozšíří z deklarace snímku [proc](../../assembler/masm/proc.md) na [. ](../../assembler/masm/dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. SAVEREG** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
