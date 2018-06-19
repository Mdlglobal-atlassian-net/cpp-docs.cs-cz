---
title: OMP_NESTED | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6b51df88ae700f81cf84250cc06ae24c9131fec
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691219"
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