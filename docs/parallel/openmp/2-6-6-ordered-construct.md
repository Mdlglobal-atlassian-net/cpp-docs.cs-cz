---
title: 2.6.6 ordered – konstrukce
ms.date: 11/04/2016
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
ms.openlocfilehash: fe6ad4adf2a4fcccfefe3c3585d9c88c0a118931
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615797"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered – konstrukce

Následující strukturovaný blok **seřazené** – direktiva je provedeny v pořadí, ve kterém by byl proveden iterací v sekvenčních smyčkách. Syntaxe **seřazené** direktivy je následující:

```
#pragma omp ordered new-linestructured-block
```

**Seřazené** direktiva musí být v rámci dynamický rozsah **pro** nebo **paralelní pro** vytvořit. **Pro** nebo **paralelní pro** direktiv, ke kterému **seřazené** musí mít konstruktor vytvoří vazbu **seřazené** klauzule zadat, jak je popsáno v [Části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11. Za běhu **pro** nebo **paralelní pro** vytvořit s **seřazené** klauzule **seřazené** konstruktory jsou spouštěny výhradně v pořadí, ve kterém by být prováděna v sekvenční provádění smyčky.

Omezení **seřazené** směrnice jsou následující:

- Iterace smyčky s **pro** konstrukce nesmí stejného seřazeného – direktiva spouštění více než jednou a nesmí spuštění, více než jeden **seřazené** směrnice.