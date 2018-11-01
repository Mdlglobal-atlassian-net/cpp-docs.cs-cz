---
title: 2.6.2 critical – konstrukce
ms.date: 11/04/2016
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
ms.openlocfilehash: dcc0e6144be5daee2a225cda621db818e5a38e2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539071"
---
# <a name="262-critical-construct"></a>2.6.2 critical – konstrukce

**Kritické** – direktiva určuje konstrukce, která omezuje spuštění přidružené strukturovaný blok na jedno vlákno v čase. Syntaxe **kritické** direktivy je následující:

```
#pragma omp critical [(name)]  new-linestructured-block
```

Volitelně *název* slouží k identifikaci důležité oblasti. Identifikátory, které slouží k identifikaci důležité oblasti mají vnější propojení a jsou v oboru názvů, který je nezávislý obory názvů používané popisky, značky, členy a běžnými identifikátory.

Vlákno čeká na začátku důležité oblasti žádné vlákno provádí důležité oblasti (kdekoli v programu) se stejným názvem. Všechny nepojmenované **kritické** direktivy namapovat na stejnou neurčené název.