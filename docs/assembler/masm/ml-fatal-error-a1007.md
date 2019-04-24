---
title: Závažná chyba nástroje ML A1007
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 98933c3a24da22f447174a3b51c4855690aba83e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177900"
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