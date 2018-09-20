---
title: 2.6.6 ordered – konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b83c3dfc13b231a1314343a1dff496acf7a99b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412194"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered – konstrukce

Následující strukturovaný blok **seřazené** – direktiva je provedeny v pořadí, ve kterém by byl proveden iterací v sekvenčních smyčkách. Syntaxe **seřazené** direktivy je následující:

```
#pragma omp ordered new-linestructured-block
```

**Seřazené** direktiva musí být v rámci dynamický rozsah **pro** nebo **paralelní pro** vytvořit. **Pro** nebo **paralelní pro** direktiv, ke kterému **seřazené** musí mít konstruktor vytvoří vazbu **seřazené** klauzule zadat, jak je popsáno v [Části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11. Za běhu **pro** nebo **paralelní pro** vytvořit s **seřazené** klauzule **seřazené** konstruktory jsou spouštěny výhradně v pořadí, ve kterém by být prováděna v sekvenční provádění smyčky.

Omezení **seřazené** směrnice jsou následující:

- Iterace smyčky s **pro** konstrukce nesmí stejného seřazeného – direktiva spouštění více než jednou a nesmí spuštění, více než jeden **seřazené** směrnice.