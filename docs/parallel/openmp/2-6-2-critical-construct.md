---
title: "2.6.2 critical – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13e9b4a8611732c7dddb81be1ca6123b725f7169
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="262-critical-construct"></a>2.6.2 critical – konstrukce
**Kritické** – direktiva identifikuje konstruktor, který omezuje provádění přidružené strukturovaných bloku na jedno vlákno najednou. Syntaxe **kritické** – Direktiva vypadá takto:  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Volitelný *název* může použít k identifikaci kritické oblasti. Identifikátory používané k identifikaci důležité oblasti mít externí propojení a jsou v oboru názvů, která je oddělená od obory názvů používá popisky, značky, členů a obyčejnou identifikátory.  
  
 Vlákno čeká na začátku důležité oblasti, dokud žádné jiné vlákno provádí důležité oblasti (kdekoli v programu) se stejným názvem. Všechny nepojmenované **kritické** direktivy mapovat stejný název neurčené.