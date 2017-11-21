---
title: "omp_get_nested – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_get_nested
dev_langs: C++
helpviewer_keywords: omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2d67008fde4d8d3093c33bfc9389004ce3b339db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ompgetnested"></a>omp_get_nested
Vrátí hodnotu, která určuje, zda je povoleno vnořené stupně paralelního zpracování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int omp_get_nested( );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je povoleno nenulové hodnoty, vnořené stupně paralelního zpracování.  
  
## <a name="remarks"></a>Poznámky  
 Vnořené paralelismus je definován s [omp_set_nested –](../../../parallel/openmp/reference/omp-set-nested.md) a [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md).  
  
 Další informace najdete v tématu [3.1.10 omp_get_nested – funkce](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).  
  
## <a name="example"></a>Příklad  
 V tématu [omp_set_nested –](../../../parallel/openmp/reference/omp-set-nested.md) příklad použití `omp_get_nested`.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../parallel/openmp/reference/openmp-functions.md)