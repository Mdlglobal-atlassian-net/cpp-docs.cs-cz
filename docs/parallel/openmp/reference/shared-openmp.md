---
title: sdílené (OpenMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 078d4b01d2c797fa11c3603c79a341f75e11f18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115473"
---
# <a name="shared-openmp"></a>shared (OpenMP)
Určuje, že jeden nebo více proměnných by měl být sdílena mezi všemi vlákny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
shared(var)  
```  
  
### <a name="parameters"></a>Parametry
  
*var*<br/>
Jeden nebo více proměnných sdílet. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.  
  
## <a name="remarks"></a>Poznámky  
 Dalším způsobem, jak sdílet proměnné mezi vlákny je [copyprivate](../../../parallel/openmp/reference/copyprivate.md) klauzuli.  
  
 `shared` platí pro následující direktivy:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.7.2.4 sdílené](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [privátní](../../../parallel/openmp/reference/private-openmp.md) pro příklad použití `shared`.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)