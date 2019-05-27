---
title: Méně závažná chyba nástroje ML A2219
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 61fa6bc6d630f1e8a8ac84492b60690c9545fb3e
ms.sourcegitcommit: 79e985d3c6e8ccaf94f6e641972887cae8c6eeb0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197680"
---
# <a name="ml-nonfatal-error-a2219"></a>Méně závažná chyba nástroje ML A2219

> Chybné zarovnání posunu v kódu uvolnění

## <a name="remarks"></a>Poznámky

Operand pro [ &period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) a [ &period;SAVEREG](../../assembler/masm/dot-savereg.md) musí být násobkem 8.  Operand pro [ &period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) a [ &period;SETFRAME](../../assembler/masm/dot-setframe.md) musí být násobkem 16.

## <a name="see-also"></a>Viz také:

[ML – chybové zprávy](../../assembler/masm/ml-error-messages.md)
