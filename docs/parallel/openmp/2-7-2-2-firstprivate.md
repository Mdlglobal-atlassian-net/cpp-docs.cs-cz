---
title: 2.7.2.2 firstprivate
ms.date: 11/04/2016
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
ms.openlocfilehash: f981c66fd3e0a2f42dcf731954f5054f96ed2973
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605969"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

**Firstprivate** klauzule nabízí nadmnožinu funkcí poskytovaných **privátní** klauzuli. Syntaxe **firstprivate** klauzule vypadá takto:

```
firstprivate(variable-list)
```

Zadané v proměnné *seznamu proměnné* mají **privátní** klauzule sémantiku, jak je popsáno v [části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25. Inicializace nebo konstrukce se stane, jako kdyby byly provést jednou na vlákno, před spuštěním podprocesu konstrukce. Pro **firstprivate** klauzuli paralelní konstrukce, počáteční hodnota nový privátní objekt je hodnota původního objektu, který existuje bezprostředně před paralelní konstrukce pro vlákno, které nalezne ho. Pro **firstprivate** je počáteční hodnota pro každé vlákno, které provádí konstruktoru work-sharing nový objekt privátní klauzule v konstruktoru work-sharing hodnota původního objektu, která existuje v čase před bodem, který stejném vlákně, zaznamená konstruktoru work-sharing. Kromě toho pro objekty C++, tento nový privátní objekt pro každé vlákno je vytvořený z původního objektu z kopie.

Omezení týkající **firstprivate** klauzule jsou následující:

- Zadané v proměnné **firstprivate** klauzule nesmí mít neúplný typ nebo typ odkazu.

- Proměnná typu třídy, který je zadán jako **firstprivate** musí mít konstruktor kopie přístupná a jednoznačná.

- Proměnné, které jsou v rámci paralelní oblasti privátní nebo které se objeví v **snížení** klauzuli **paralelní** směrnice nelze zadat v **firstprivate** klauzuli sdílení práce – direktiva s vazbou na paralelní konstrukce.