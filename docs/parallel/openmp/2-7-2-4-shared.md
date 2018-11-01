---
title: 2.7.2.4 shared
ms.date: 11/04/2016
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
ms.openlocfilehash: ae470f4be67fac57146017d3e2791f6f95aa61b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583440"
---
# <a name="2724-shared"></a>2.7.2.4 shared

Tato klauzule sdílí proměnné, které se zobrazují v *seznamu proměnné* mezi všemi vlákny v týmu. Všechna vlákna v rámci týmu přístup do stejné oblasti úložiště pro **sdílené** proměnné.

Syntaxe **sdílené** klauzule vypadá takto:

```
shared(variable-list)
```