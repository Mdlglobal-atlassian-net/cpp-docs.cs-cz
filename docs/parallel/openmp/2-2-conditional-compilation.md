---
title: 2.2 Podmíněná kompilace
ms.date: 11/04/2016
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
ms.openlocfilehash: 9dc107ee9e5328df205d4b6f826f71c23abfb3ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658546"
---
# <a name="22-conditional-compilation"></a>2.2 Podmíněná kompilace

_**OPENMP** – makro název je definován implementací CLS OpenMP jako desítkovou konstantu *yyyymm*, která bude roku a měsíce specifikace schválené. Toto makro nesmí být předmět **#define** nebo **#undef** direktiva předzpracování.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Pokud dodavatelů definovat rozšíření pro OpenMP, určují další předdefinovaná makra.