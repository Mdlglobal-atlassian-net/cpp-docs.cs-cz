---
title: Závažná chyba nástroje ML A1007
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 01633b4fa084b7d5e14af5a5c6e51e3dca684d2a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856914"
---
# <a name="ml-fatal-error-a1007"></a>Závažná chyba nástroje ML A1007

**příliš hluboká úroveň vnořování**

Assembler dosáhl svého limitu vnořování. Limit je 20 úrovní s výjimkou případů, kdy je uvedeno jinak.

Jedna z následujících možností byla vnořena příliš hluboko:

- Direktiva vysoké úrovně, například [. Pokud](../../assembler/masm/dot-if.md), [. Opakujte akci](../../assembler/masm/dot-repeat.md), nebo [. WHILe](../../assembler/masm/dot-while.md).

- Definice struktury.

- Direktiva podmíněného sestavení.

- Definice procedury.

- Direktiva [PUSHCONTEXT](../../assembler/masm/pushcontext.md) (limit je 10).

- Definice segmentu.

- Soubor zahrnutí.

- Makro.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>