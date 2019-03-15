---
title: Odvozené závislé objekty a pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: b9c3055db0cc173999e1737986166eb334dcf96c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823129"
---
# <a name="inferred-dependents-and-rules"></a>Odvozené závislé objekty a pravidla

NMAKE předpokládá odvozené závislé pro cíl, pokud existuje pravidlo použít odvození. Některé pravidlo použije, pokud:

- *toext* odpovídá rozšíření cíle.

- *fromext* shody přípony souboru, který má základní název cíle a, která existuje v adresáři aktuální nebo zadané.

- *fromext* probíhá [. PŘÍPONY](dot-directives.md); žádné jiné *fromext* v odpovídající pravidlo má vyšší **. PŘÍPONY** priority.

- Nemá žádné explicitní závislé na vyšší **. PŘÍPONY** priority.

Odvozené závislé objekty může způsobit neočekávané vedlejší účinky. Pokud cílový blok popis obsahuje příkazy, NMAKE provede tyto příkazy místo příkazy v pravidle.

## <a name="see-also"></a>Viz také:

[Odvozená pravidla](inference-rules.md)
