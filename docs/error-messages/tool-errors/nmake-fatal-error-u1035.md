---
title: Závažná chyba nástroje NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324334"
---
# <a name="nmake-fatal-error-u1035"></a>Závažná chyba nástroje NMAKE U1035

Chyba syntaxe: byl očekáván ':' nebo '=' oddělovač

Buď dvojtečkou (**:**) nebo znaménko rovná se (**=**) byl očekáván.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Dvojtečka neřídil cíl.

1. Dvojtečka a žádná mezera (například a:) a potom písmeno jeden cíl. NMAKE je interpretován jako specifikaci jednotky.

1. Dvojtečka neřídil odvozené pravidlo.

1. Definice makra nenásledovala znaménko rovná se.

1. Znak za zpětným lomítkem (**\\**), která byla použita pokračujte příkaz na nový řádek.

1. Řetězec, který neřídil jakékoli pravidlo syntaxe NMAKE se objevil.

1. Souboru pravidel se formátované textový procesor.