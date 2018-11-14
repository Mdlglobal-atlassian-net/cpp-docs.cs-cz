---
title: 2.7.2.8 copyprivate
ms.date: 11/04/2016
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
ms.openlocfilehash: f46b8ae1d42083c770bbc84c46d13b02d5227498
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521853"
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