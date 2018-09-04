---
title: Závažná méně závažná chyba nástroje ML A2006 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f287c6ab46c6af71ba6dc0032f332ce3cc489454
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677402"
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