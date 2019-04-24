---
title: Méně závažná chyba nástroje ML A2006
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 80283bde4dff36e32d276c998f6797b6eeed8160
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202320"
---
# <a name="ml-nonfatal-error-a2006"></a>Méně závažná chyba nástroje ML A2006

**Nedefinovaný symbol: identifikátor**

Byl proveden pokus o použití symbolu, který nebyl definován.

Jednu z následujících mohlo dojít:

- Symbol není definovaný.

- Pole nebylo člen zadané struktury.

- Symbol byl definován v zahrnutém souboru, který není zahrnutý.

- Externí symbol se použil bez [EXTERN](../../assembler/masm/extern-masm.md) nebo [EXTERNDEF](../../assembler/masm/externdef.md) směrnice.

- Bylo zadáno chybně název symbolu.

- Popisek místní kódu bylo odkazováno mimo svůj rozsah.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>