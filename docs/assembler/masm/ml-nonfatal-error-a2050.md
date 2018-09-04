---
title: Méně závažná chyba nástroje ML A2050 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd2e0e6c2fc818ef9286fd303c07a26bdd8b4e5a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680668"
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