---
title: OMP_DYNAMIC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de4a81d861bf72943a67356577da37c36df63f69
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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