---
title: 2.7.2.8 copyprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6815afe12344f94ed33d6b9260472f3e29eb72a0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406357"
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

**Copyprivate** klauzule poskytuje mechanismus pro používat soukromé proměnné k ostatním členům vysílání hodnotu z jednoho člena týmu. Jde o alternativu k použití sdílené proměnné pro hodnotu při poskytování sdílené proměnné by bylo obtížné (například v rekurze vyžadující jinou proměnnou na každé úrovni). **Copyprivate** klauzule může vyskytovat jenom u **jeden** směrnice.

Syntaxe **copyprivate** klauzule vypadá takto:

```

copyprivate(
variable-list
)

```

Účinek **copyprivate** klauzuli pro proměnné ve svém seznamu proměnné dojde poté, co provádění strukturovaný blok přidružené **jeden** sestavit a před jakoukoli vlákna odbourejte překážky bránící na konci konstrukce ještě zbývá týmu. Pak na všechna vlákna v týmu pro každou proměnnou v *seznamu proměnné*, tato proměnná změní určené (jako přiřazení) s odpovídající hodnotou proměnné ve vlákně, který spouští konstrukce uživatele strukturované blok.

Omezení **copyprivate** klauzule jsou následující:

- Proměnná, která je zadána v **copyprivate** klauzule nesmí být v **privátní** nebo **firstprivate** klauzule pro stejný **jedním**směrnice.

- Pokud **jeden** s **copyprivate** klauzule narazí na dynamický rozsah paralelní oblasti, všechny proměnné zadané v **copyprivate** klauzule musí být v rámci nadřazeného privátní.

- Proměnná, která je zadána v **copyprivate** klauzule musí mít přístupné jednoznačný kopírovacího operátoru přiřazení.