---
title: Méně závažná chyba nástroje ML A2050
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 59d08b9c2743a3b45633527bcc54b3e1c4d6a58c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177549"
---
# <a name="ml-nonfatal-error-a2050"></a>Méně závažná chyba nástroje ML A2050

**Real nebo není povolený počet konfiguračních dat spouštění**

Číslo s plovoucí desetinnou čárkou (skutečné) nebo konstanta desetinné programového binární soubor (BCD) byla použita jiné než jako inicializátor data.

Došlo k jedné z následujících akcí:

- Reálné číslo nebo BCD byla použita ve výrazu.

- Reálné číslo byla použita k inicializaci jiné než direktivu [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), nebo [TBYTE](../../assembler/masm/tbyte.md).

- BCD byla použita k inicializaci jiné než direktivu `TBYTE`.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>