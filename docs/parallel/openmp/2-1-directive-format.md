---
title: "2.1 formát direktivy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5760c4ccd3fcaf036f0d6d0aef09d29bbbaf8862
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="21-directive-format"></a>2.1 Formát direktivy
Syntaxe direktivy OpenMP oficiálně určeného gramatiku v [příloha C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)a neformálně následujícím způsobem:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Každý – direktiva začíná **omp – #pragma**, abychom předešli pro jsou v konfliktu s další direktivy pragma (bez OpenMP nebo dodavatele rozšíření OpenMP) se stejnými názvy. Zbývající část direktiva dodržovat konvence prostředí standardů C a C++ pro direktivy kompilátoru. Konkrétně mezer lze před a po  **#** , a někdy mezer musí být použit k oddělení slova v direktivu. Předběžné zpracování tokeny následující **#pragma omp –** podléhají makro nahrazení.  
  
 Direktivy rozlišují velká a malá písmena. Pořadí, ve kterém klauzule zobrazují v direktivy není důležité. Klauzule na direktivy může podle potřeby, podléhají omezením uvedených v popisu jednotlivých klauzule opakovat. Pokud *seznamu proměnné* se zobrazí v klauzuli, musí určovat pouze proměnné. Pouze jeden *– direktiva název* jeden – direktiva lze zadat.  Například následující direktiva nesmí:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP – direktiva se vztahuje na maximálně jeden všechna následující příkaz, který musí být strukturovaný blok.