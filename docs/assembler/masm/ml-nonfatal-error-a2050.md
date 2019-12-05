---
title: Méně závažná chyba nástroje ML A2050
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 15c6449ff4207c92dee28120d4f61be641cf01c8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856574"
---
# <a name="ml-nonfatal-error-a2050"></a>Méně závažná chyba nástroje ML A2050

**reálné číslo nebo číslo BCD není povolené.**

Bylo použito číslo s plovoucí desetinnou čárkou (reálné) nebo binární kódování desítkové soustavy (BCD) jiné než jako inicializátor dat.

Došlo k jedné z následujících:

- Ve výrazu se použilo reálné číslo nebo BCD.

- Reálné číslo bylo použito k inicializaci jiné direktivy než [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md)nebo [TBYTE](../../assembler/masm/tbyte.md).

- Používala se BCD k inicializaci jiné direktivy než `TBYTE`.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>