---
title: Odvozené závislé objekty a pravidla | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c13ae7784ff40b39642ce26fd062a1aab80f2d4c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707548"
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