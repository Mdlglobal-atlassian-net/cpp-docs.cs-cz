---
title: OMP_DYNAMIC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fcff25541921ccac9dc2e205480dc6277f620b1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ompdynamic"></a>OMP_DYNAMIC
Určuje, zda OpenMP běh můžete upravit počet vláken v paralelní oblasti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Poznámky  
 `OMP_DYNAMIC` – Proměnná prostředí je možné přepsat [omp_set_dynamic –](../../../parallel/openmp/reference/omp-set-dynamic.md) funkce.  
  
 Výchozí hodnota v implementaci Visual C++ standardní OpenMP je `OMP_DYNAMIC=FALSE`.  
  
 Další informace najdete v tématu [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz nastaví `OMP_DYNAMIC` proměnnou prostředí na hodnotu TRUE:  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 Následující příkaz zobrazí aktuální nastavení `OMP_DYNAMIC` proměnnou prostředí:  
  
```  
set OMP_DYNAMIC  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)