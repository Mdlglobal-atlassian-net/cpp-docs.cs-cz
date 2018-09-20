---
title: 2.7.2.3 lastprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25edca8391eb094691ef4fea3c360d351f979b43
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385960"
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