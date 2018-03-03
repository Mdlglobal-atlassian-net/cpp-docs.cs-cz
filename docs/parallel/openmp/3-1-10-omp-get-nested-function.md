---
title: "3.1.10 omp_get_nested – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36b213ee45018e7cc0ccf3a1cb99dcbd640d4457
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested – funkce
`omp_get_nested` Funkce vrátí nenulovou hodnotu, pokud je povoleno vnořené paralelismus a 0, pokud je zakázána. Další informace o vnořené paralelismus najdete na stránce 40 části 3.1.9. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Implementace neimplementuje vnořené paralelismus, tato funkce vždy vrátí hodnotu 0.