---
title: Závažná chyba nástroje ML A1007 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 539ab431510d5dc721e6531c11069a87e27c287a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693598"
---
# <a name="ml-fatal-error-a1007"></a>Závažná chyba nástroje ML A1007

**úroveň vnoření příliš hluboké**

Assembler dosáhla svého limitu vnořování. Limit je 20 úrovně není uvedeno jinak.

Byl jeden z následujících akcí jsou vnořené moc hluboko:

- Direktivu vysoké úrovně, jako [. Pokud](../../assembler/masm/dot-if.md), [. OPAKUJTE](../../assembler/masm/dot-repeat.md), nebo [. ZATÍMCO](../../assembler/masm/dot-while.md).

- Definice struktury.

- Direktivy podmíněné sestavení.

- Definice procedury.

- A [PUSHCONTEXT](../../assembler/masm/pushcontext.md) – direktiva (limit je 10).

- Definice segmentu.

- Soubor zahrnutí.

- Makra.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>