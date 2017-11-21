---
title: OMP_DYNAMIC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_DYNAMIC
dev_langs: C++
helpviewer_keywords: OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5c416919678cd7b0f80bd1299c7682fe159cd19
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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