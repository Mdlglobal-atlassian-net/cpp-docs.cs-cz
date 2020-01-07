---
title: Méně závažná chyba nástroje ML A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 311aedd0cc739fd862efb0a18cc444b3fb75b165
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316977"
---
# <a name="ml-nonfatal-error-a2050"></a>Méně závažná chyba nástroje ML A2050

**reálné číslo nebo číslo BCD není povolené.**

Bylo použito číslo s plovoucí desetinnou čárkou (reálné) nebo binární kódování desítkové soustavy (BCD) jiné než jako inicializátor dat.

Došlo k jedné z následujících:

- Ve výrazu se použilo reálné číslo nebo BCD.

- Reálné číslo bylo použito k inicializaci jiné direktivy než [DWORD](dword.md), [QWORD](qword.md)nebo [TBYTE](tbyte.md).

- Používala se BCD k inicializaci jiné direktivy než `TBYTE`.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
