---
title: "Odvozené závislé objekty a pravidla | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe7c49607f466d8fd1d333883414b24d7837432b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inferred-dependents-and-rules"></a>Odvozené závislé objekty a pravidla
NMAKE předpokládá odvozené závislé pro cíl, pokud se pravidlo vztahuje odvození existuje. Pravidlo platí, pokud:  
  
-   *toext* odpovídá cílové složky rozšíření.  
  
-   *fromext* odpovídá přípona souboru, který má základní název cílové složky a který existuje v adresáři zadané nebo aktuální.  
  
-   *fromext* v [. PŘÍPONY](../build/dot-directives.md); žádný jiný *fromext* v odpovídající pravidlo, má vyššího **. PŘÍPONY** s prioritou.  
  
-   Žádné explicitní závislé má vyššího **. PŘÍPONY** s prioritou.  
  
 Odvozené závislé objekty může způsobit neočekávané vedlejší účinky. Pokud cílový popis blok obsahuje příkazy, NMAKE spouští tyto příkazy místo příkazy v pravidle.  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)