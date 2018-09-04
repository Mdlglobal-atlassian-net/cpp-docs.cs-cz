---
title: Závažná méně závažná chyba nástroje ML A2096 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f4ef76dca10b1208a931bc3e1cc09d82a639d2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679595"
---
# <a name="ml-nonfatal-error-a2096"></a>Méně závažná chyba nástroje ML A2096

**Segment, skupiny nebo registr segmentu očekávání**

Segment nebo skupiny očekávala, ale nebyl nalezen.

Došlo k jedné z následujících akcí:

- Levý operand zadané segmentu přepsat – operátor (**:**) nebyla segmentu registr (CS, DS, SS, ES, FS nebo GS), název skupiny, název segmentu nebo výraz segmentu.

- [Předpokládat](../../assembler/masm/assume.md) směrnice byl zadán segment registrace bez adresu platnou segmentu, registr segmentu, skupiny nebo speciální **PLOCHÝ** skupiny.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>