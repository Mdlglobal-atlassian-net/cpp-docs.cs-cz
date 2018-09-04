---
title: Závažná chyba nástroje ML A1010 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12b7e8698951e8ef59e0433134ec992af5d5f77f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676294"
---
# <a name="ml-fatal-error-a1010"></a>Závažná chyba nástroje ML A1010

**vnoření bezkonkurenční blok:**

Začátek bloku neměl odpovídajícího end nebo koncový blok nemá odpovídající začátku. Možné zahrnutí jednu z následujících akcí:

- Direktivu vysoké úrovně, jako [. Pokud](../../assembler/masm/dot-if.md), [. OPAKUJTE](../../assembler/masm/dot-repeat.md), nebo [. ZATÍMCO](../../assembler/masm/dot-while.md).

- Direktivy podmíněné sestavení jako [IF](../../assembler/masm/if-masm.md), [OPAKUJTE](../../assembler/masm/repeat.md), nebo **při**.

- Definici struktury nebo sjednocení.

- Definice procedury.

- Definice segmentu.

- A [POPCONTEXT](../../assembler/masm/popcontext.md) směrnice.

- Podmíněné sestavení direktiv, například [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), nebo **ENDIF** bez odpovídajícího [IF](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>