---
title: Závažná chyba nástroje ML A1008 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1008
dev_langs:
- C++
helpviewer_keywords:
- A1008
ms.assetid: fe592f9d-c37b-4cd8-a51d-e3c15ddcab83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec709823856e17c90d4af2a06262b30c966f39c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691935"
---
# <a name="ml-fatal-error-a1008"></a>Závažná chyba nástroje ML A1008

**vnoření bezkonkurenční – makro**

Buď makro nebyl ukončen před koncem souboru nebo direktivě ukončující [ENDM](../../assembler/masm/endm.md) byl nalezen mimo blok – makro.

Jednou z příčin této chyby je vynechání tečka před [. OPAKUJTE](../../assembler/masm/dot-repeat.md) nebo [. ZATÍMCO](../../assembler/masm/dot-while.md).

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>