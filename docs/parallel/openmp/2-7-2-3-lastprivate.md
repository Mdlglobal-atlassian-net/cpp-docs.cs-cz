---
title: 2.7.2.3 lastprivate
ms.date: 11/04/2016
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
ms.openlocfilehash: 15f9af23c4f4e1c0ce2914a979f7a41e7b4a6bc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428455"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate` Klauzule nabízí nadmnožinu funkcí poskytovaných `private` klauzuli. Syntaxe `lastprivate` klauzule vypadá takto:

```
lastprivate(variable-list)
```

Zadané v proměnné *seznamu proměnné* mají `private` klauzule sémantiku. Při `lastprivate` klauzule se zobrazí v direktivě, který identifikuje konstruktoru work-sharing, hodnotu každého `lastprivate` přiřadí proměnná z postupně poslední iterace přidružené smyčky nebo lexikálně poslední direktivu section proměnné původní objekt. Proměnné, které nejsou přiřazeny hodnoty podle poslední iterace **pro** nebo **paralelní pro**, nebo lexikálně poslední část **oddíly** nebo  **Parallel sections –** směrnice, mají neurčité hodnoty po vytvoření. Nepřiřazené podobjekty také mají neurčité hodnoty po vytvoření.

Omezení týkající `lastprivate` klauzule jsou následující:

- Všechna omezení pro `private` použít.

- Proměnná typu třídy, který je zadán jako `lastprivate` musí mít operátor přiřazení kopie přístupná a jednoznačná.

- Proměnné, které jsou v rámci paralelní oblasti privátní nebo které se objeví v `reduction` klauzuli **paralelní** směrnice nelze zadat v `lastprivate` klauzuli direktivy sdílení práce, s vazbou na paralelní konstrukce.