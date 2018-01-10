---
title: "OpenMP – knihovny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c0f009c26789fd771d55dab5fcfe5f342aa03b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-libraries"></a>OpenMP – knihovny
Popisuje soubory .lib, které tvoří běhové knihovny OpenMP ve Visual C++.  
  
 Následující knihovny obsahují funkce běhové knihovny Visual C++ OpenMP.  
  
|OpenMP běhové knihovny|Vlastnosti|  
|------------------------------|---------------------|  
|VCOMP. LIB|Více vláken, dynamického propojení (knihovna importu pro VCOMP. LIB).|  
|VCOMPD. LIB|Více vláken, dynamického propojení (knihovna importu pro VCOMPD. KRYTU) (ladění)|  
  
 Pokud _DEBUG – je definována v kompilaci a `#include omp.h` je ve zdrojovém kódu, VCOMPD. LIB bude výchozí lib. V opačném VCOMP. LIB se použije.  
  
 Můžete použít [/NODEFAULTLIB (Ignorovat knihovny)](../../../build/reference/nodefaultlib-ignore-libraries.md) a odeberte výchozí lib explicitně propojit s lib podle svého výběru.  
  
 Knihovny DLL OpenMP jsou v adresáři Visual C++ redistributable a nutné distribuovat s aplikací, které používají OpenMP.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)