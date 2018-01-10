---
title: "_CRT_DISABLE_PERFCRIT_LOCKS – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs: C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07962266c94743968ff407aa5be78f66e189f6aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS
Zakáže výkonu kritické zamykání v vstupně-výstupních operací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## <a name="remarks"></a>Poznámky  
 Definování tento symbol může zlepšit výkon v jednovláknové programy I/čítači vynucením všechny vstupně-výstupních operací předpokládat, že model jednovláknové vstupně-výstupní operace. Další informace najdete v tématu [vícevláknové knihovny výkonu](../c-runtime-library/multithreaded-libraries-performance.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)