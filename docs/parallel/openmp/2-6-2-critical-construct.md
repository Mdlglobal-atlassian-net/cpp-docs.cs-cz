---
title: 2.6.2 critical – konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e51bd425999081c7a06a7d5692dbea16c887fa0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417849"
---
# <a name="262-critical-construct"></a>2.6.2 critical – konstrukce

**Kritické** – direktiva určuje konstrukce, která omezuje spuštění přidružené strukturovaný blok na jedno vlákno v čase. Syntaxe **kritické** direktivy je následující:

```
#pragma omp critical [(name)]  new-linestructured-block
```

Volitelně *název* slouží k identifikaci důležité oblasti. Identifikátory, které slouží k identifikaci důležité oblasti mají vnější propojení a jsou v oboru názvů, který je nezávislý obory názvů používané popisky, značky, členy a běžnými identifikátory.

Vlákno čeká na začátku důležité oblasti žádné vlákno provádí důležité oblasti (kdekoli v programu) se stejným názvem. Všechny nepojmenované **kritické** direktivy namapovat na stejnou neurčené název.