---
title: OMP_NESTED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NESTED
dev_langs: C++
helpviewer_keywords: OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 911ccd3e03b2d9d7f7fa14f01a8cbf0d166832d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ompnested"></a>OMP_NESTED
Určuje, zda je vnořené paralelismus povoleno, není-li povoleno nebo zakázáno s vnořené paralelismus `omp_set_nested`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Poznámky  
 `OMP_NESTED` – Proměnná prostředí je možné přepsat [omp_set_nested –](../../../parallel/openmp/reference/omp-set-nested.md) funkce.  
  
 Výchozí hodnota v implementaci Visual C++ standardní OpenMP je `OMP_DYNAMIC=FALSE`.  
  
 Další informace najdete v tématu [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz nastaví `OMP_NESTED` proměnnou prostředí na hodnotu TRUE:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 Následující příkaz zobrazí aktuální nastavení `OMP_NESTED` proměnnou prostředí:  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)