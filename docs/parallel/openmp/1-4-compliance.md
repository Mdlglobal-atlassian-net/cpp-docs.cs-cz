---
title: "1.4 dodržování předpisů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8481c0efb54a397db004f321fb48c217cba8ebc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="14-compliance"></a>1.4 Kompatibilita
Implementace rozhraní API jazyka C/C++ OpenMP je *kompatibilní se standardem OpenMP* pokud ji rozpozná a zachová sémantika všechny elementy této specifikace, který je uveden v kapitolách 1, 2, 3, 4, a příloha C. přílohy A, B, D, E a F jsou pro informace pouze účely a nejsou součástí specifikace. Implementace, které zahrnují jenom podmnožinu rozhraní API nejsou kompatibilní se standardem OpenMP.  
  
 OpenMP C a C++ API je rozšíření základní jazyk, který podporuje implementace. Pokud základní jazyk nepodporuje jazyk konstrukce nebo rozšíření, která se zobrazí v tomto dokumentu, implementace OpenMP není potřeba ho podporují.  
  
 Všechny standardní funkce knihovny jazyka C a C++ a integrované funkce (to znamená, ve kterých má kompilátor specifické znalosti funkce) musí být bezpečné pro přístup z více vláken. Nesynchronizované použití funkcí vláken podle různých vláknech uvnitř paralelní oblast nevytváří nedefinované chování. Chování však nemusí být stejný jako sériové oblast. (Náhodné číslo funkce generování je příklad).  
  
 Rozhraní API jazyka C/C++ OpenMP Určuje, že určité chování *definované implementací.* Vyhovující provedení OpenMP je potřeba definovat a zdokumentovat své chování v těchto případech. V tématu [příloha E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), stránka 97 seznam chování definované implementací.