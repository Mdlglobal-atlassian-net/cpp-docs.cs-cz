---
title: "OpenMP – knihovny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 760e7d138ab71244419ff71960948d4d10f125eb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="openmp-libraries"></a>OpenMP – knihovny
Popisuje soubory .lib, které tvoří běhové knihovny OpenMP ve Visual C++.  
  
 Následující knihovny obsahují funkce běhové knihovny Visual C++ OpenMP.  
  
|OpenMP běhové knihovny|Vlastnosti|  
|------------------------------|---------------------|  
|VCOMP.LIB|Více vláken, dynamického propojení (knihovna importu pro VCOMP. LIB).|  
|VCOMPD.LIB|Více vláken, dynamického propojení (knihovna importu pro VCOMPD. KRYTU) (ladění)|  
  
 Pokud _DEBUG – je definována v kompilaci a `#include omp.h` je ve zdrojovém kódu, VCOMPD. LIB bude výchozí lib. V opačném VCOMP. LIB se použije.  
  
 Můžete použít [/NODEFAULTLIB (Ignorovat knihovny)](../../../build/reference/nodefaultlib-ignore-libraries.md) a odeberte výchozí lib explicitně propojit s lib podle svého výběru.  
  
 Knihovny DLL OpenMP jsou v adresáři Visual C++ redistributable a nutné distribuovat s aplikací, které používají OpenMP.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)