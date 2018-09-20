---
title: 2.7.2.2 firstprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e6ad966f4cf895da9374798f6c9a4079ccc2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400962"
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