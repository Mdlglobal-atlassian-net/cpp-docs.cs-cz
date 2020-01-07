---
title: Méně závažná chyba nástroje ML A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 611be49a1d4018eeb4edd9ee750d5a0614a83abe
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311946"
---
# <a name="ml-nonfatal-error-a2219"></a>Méně závažná chyba nástroje ML A2219

> Chybné zarovnání pro posun v unwind kódu

## <a name="remarks"></a>Poznámky

Operandem [&period;ALLOCSTACK](dot-allocstack.md) a [&period;SAVEREG](dot-savereg.md) musí být násobkem 8.  Operandem [&period;SAVEXMM128](dot-savexmm128.md) a [&period;SETFRAME](dot-setframe.md) musí být násobek 16.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
