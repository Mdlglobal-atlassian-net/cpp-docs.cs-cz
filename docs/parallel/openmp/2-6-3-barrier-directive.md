---
title: "2.6.3 barrier – direktiva | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9c64787d9c6cc2dd0809f75f8f9db9819174d0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="263-barrier-directive"></a>2.6.3 barrier – direktiva
**Barrier** – direktiva synchronizuje všechna vlákna v týmu. Pokud došlo, každé vlákno v týmu počká, až všechny ostatní dosáhli tento bod. Syntaxe **barrier** – Direktiva vypadá takto:  
  
```  
#pragma omp barrier new-line  
```  
  
 Až v týmu všechna vlákna narazili bariéry, začne každé vlákno v týmu, provádění příkazy po direktiva bariéry paralelně. Všimněte si, že **barrier** – direktiva nemá příkaz jazyka C jako součást jeho syntaxe, platí určitá omezení na jeho umístění v rámci programu. V tématu [příloha C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pro formální gramatika. Následující příklad znázorňuje tato omezení.  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```