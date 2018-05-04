---
title: _CRT_DISABLE_PERFCRIT_LOCKS – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs:
- C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 128403009595d85e44007d79c9110b5df530b45e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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