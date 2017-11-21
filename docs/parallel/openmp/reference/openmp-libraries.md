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
ms.openlocfilehash: faac1a2a081a2ce0b02f2008bf3766537557df28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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