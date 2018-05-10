---
title: 3.1.6 omp_in_parallel – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22b491695d2ae49336d7d8998af64e724f344d87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel – funkce
**Omp_in_parallel –** funkce vrátí nenulovou hodnotu, pokud je volána v rámci dynamické rozsah oblast paralelní provádění paralelně; jinak vrátí hodnotu 0. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Tato funkce vrátí nenulovou hodnotu, když je volána v rámci oblasti provádění paralelně, včetně vnořené oblastí, které jsou serializovány.