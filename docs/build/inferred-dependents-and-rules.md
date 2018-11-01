---
title: Odvozené závislé objekty a pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 6d2f439a0e936b06012045c62d55b6ad76e5817d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548899"
---
# <a name="inferred-dependents-and-rules"></a>Odvozené závislé objekty a pravidla

NMAKE předpokládá odvozené závislé pro cíl, pokud existuje pravidlo použít odvození. Některé pravidlo použije, pokud:

- *toext* odpovídá rozšíření cíle.

- *fromext* shody přípony souboru, který má základní název cíle a, která existuje v adresáři aktuální nebo zadané.

- *fromext* probíhá [. PŘÍPONY](../build/dot-directives.md); žádné jiné *fromext* v odpovídající pravidlo má vyšší **. PŘÍPONY** priority.

- Nemá žádné explicitní závislé na vyšší **. PŘÍPONY** priority.

Odvozené závislé objekty může způsobit neočekávané vedlejší účinky. Pokud cílový blok popis obsahuje příkazy, NMAKE provede tyto příkazy místo příkazy v pravidle.

## <a name="see-also"></a>Viz také

[Odvozená pravidla](../build/inference-rules.md)