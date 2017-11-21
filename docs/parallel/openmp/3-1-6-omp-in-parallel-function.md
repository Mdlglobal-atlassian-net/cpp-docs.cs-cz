---
title: "3.1.6 omp_in_parallel – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b72351095fd56ae6543c2ca742983eef315f2158
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel – funkce
**Omp_in_parallel –** funkce vrátí nenulovou hodnotu, pokud je volána v rámci dynamické rozsah oblast paralelní provádění paralelně; jinak vrátí hodnotu 0. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Tato funkce vrátí nenulovou hodnotu, když je volána v rámci oblasti provádění paralelně, včetně vnořené oblastí, které jsou serializovány.