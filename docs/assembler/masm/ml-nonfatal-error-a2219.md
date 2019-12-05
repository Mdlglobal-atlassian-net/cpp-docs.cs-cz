---
title: Méně závažná chyba nástroje ML A2219
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: cf2be5db2aa9c21597c199a6840f4aaa50e0a681
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854586"
---
# <a name="ml-nonfatal-error-a2219"></a>Méně závažná chyba nástroje ML A2219

> Chybné zarovnání pro posun v unwind kódu

## <a name="remarks"></a>Poznámky

Operandem [&period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) a [&period;SAVEREG](../../assembler/masm/dot-savereg.md) musí být násobkem 8.  Operandem [&period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) a [&period;SETFRAME](../../assembler/masm/dot-setframe.md) musí být násobek 16.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)
