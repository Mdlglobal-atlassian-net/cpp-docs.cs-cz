---
title: Závažná chyba nástroje NMAKE U1035 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0383bf4742d637d669070efa5370ebda0c7ab159
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019858"
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