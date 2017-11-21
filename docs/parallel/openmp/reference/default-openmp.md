---
title: "Výchozí (OpenMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: default
dev_langs: C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: caafb7818c32dad7b21ac7a05d10f77753c1da73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="default-openmp"></a>default (OpenMP)
Určuje chování bez ohledu na obor proměnné v paralelní oblasti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
default(shared | none)  
```  
  
## <a name="remarks"></a>Poznámky  
 `shared`, který je v platnosti Pokud `default` není zadána klauzule, znamená, že všechny proměnné v paralelní oblasti, jako kdyby byly zadány s považovat [sdílené](../../../parallel/openmp/reference/shared-openmp.md) klauzule. `none`znamená, že všechny proměnné používané v paralelní oblasti, která nejsou obor s [privátní](../../../parallel/openmp/reference/private-openmp.md), [sdílené](../../../parallel/openmp/reference/shared-openmp.md), [snížení](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), nebo [lastprivate](../../../parallel/openmp/reference/lastprivate.md) klauzule způsobí chybu kompilátoru.  
  
 `default`platí pro následující direktivy:  
  
-   [paralelní](../../../parallel/openmp/reference/parallel.md)  
  
-   [pro](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.7.2.5 výchozí](../../../parallel/openmp/2-7-2-5-default.md).  
  
## <a name="example"></a>Příklad  
 V tématu [privátní](../../../parallel/openmp/reference/private-openmp.md) příklad použití `default`.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)