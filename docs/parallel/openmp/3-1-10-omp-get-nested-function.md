---
title: 3.1.10 omp_get_nested – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f447da6957cb385ace918120eb7ed7a5420e9f0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested – funkce
`omp_get_nested` Funkce vrátí nenulovou hodnotu, pokud je povoleno vnořené paralelismus a 0, pokud je zakázána. Další informace o vnořené paralelismus najdete na stránce 40 části 3.1.9. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Implementace neimplementuje vnořené paralelismus, tato funkce vždy vrátí hodnotu 0.