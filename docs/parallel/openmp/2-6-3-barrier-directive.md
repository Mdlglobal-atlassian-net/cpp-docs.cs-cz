---
title: "2.6.3 barrier – direktiva | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: adc480a82668da3c3ad7fdb88a701b3fa80ae9e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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