---
title: 2.6.2 critical – konstrukce | Microsoft Docs
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
ms.openlocfilehash: ae7070fcc590307e71b0c34259bcbe1c12200550
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="262-critical-construct"></a>2.6.2 critical – konstrukce
**Kritické** – direktiva identifikuje konstruktor, který omezuje provádění přidružené strukturovaných bloku na jedno vlákno najednou. Syntaxe **kritické** – Direktiva vypadá takto:  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Volitelný *název* může použít k identifikaci kritické oblasti. Identifikátory používané k identifikaci důležité oblasti mít externí propojení a jsou v oboru názvů, která je oddělená od obory názvů používá popisky, značky, členů a obyčejnou identifikátory.  
  
 Vlákno čeká na začátku důležité oblasti, dokud žádné jiné vlákno provádí důležité oblasti (kdekoli v programu) se stejným názvem. Všechny nepojmenované **kritické** direktivy mapovat stejný název neurčené.