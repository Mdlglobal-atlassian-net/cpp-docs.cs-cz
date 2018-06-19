---
title: 2.1 formát direktivy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eec5a2f0e91df6e8d71797199bd3a3911a3aab0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687268"
---
# <a name="21-directive-format"></a>2.1 Formát direktivy
Syntaxe direktivy OpenMP oficiálně určeného gramatiku v [příloha C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)a neformálně následujícím způsobem:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Každý – direktiva začíná **omp – #pragma**, abychom předešli pro jsou v konfliktu s další direktivy pragma (bez OpenMP nebo dodavatele rozšíření OpenMP) se stejnými názvy. Zbývající část direktiva dodržovat konvence prostředí standardů C a C++ pro direktivy kompilátoru. Konkrétně mezer lze před a po **#**, a někdy mezer musí být použit k oddělení slova v direktivu. Předběžné zpracování tokeny následující **#pragma omp –** podléhají makro nahrazení.  
  
 Direktivy rozlišují velká a malá písmena. Pořadí, ve kterém klauzule zobrazují v direktivy není důležité. Klauzule na direktivy může podle potřeby, podléhají omezením uvedených v popisu jednotlivých klauzule opakovat. Pokud *seznamu proměnné* se zobrazí v klauzuli, musí určovat pouze proměnné. Pouze jeden *– direktiva název* jeden – direktiva lze zadat.  Například následující direktiva nesmí:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP – direktiva se vztahuje na maximálně jeden všechna následující příkaz, který musí být strukturovaný blok.