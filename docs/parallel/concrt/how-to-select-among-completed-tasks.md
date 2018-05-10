---
title: 'Postupy: výběr z dokončených úloh | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a485eb87f2caa62a382983c1cda2b9c098742d42
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-select-among-completed-tasks"></a>Postupy: Výběr z dokončených úloh
Tento příklad ukazuje způsob použití [concurrency::choice](../../parallel/concrt/reference/choice-class.md) a [concurrency::join](../../parallel/concrt/reference/join-class.md) třídy vyberte první úlohy k dokončení vyhledávacího algoritmu.  
  
## <a name="example"></a>Příklad  
 Následující příklad provede dva algoritmy vyhledávání paralelně a vybere první algoritmus pro dokončení. Tento příklad definuje `employee` typu, který obsahuje identifikační číslo a mzda pro zaměstnance. `find_employee` Funkce najde první zaměstnanec, který má zadaný identifikátor nebo zadaná mzda. `find_employee` Funkce také obstará případu, kdy žádný zaměstnanec má zadaný identifikátor nebo mzda. `wmain` Funkce vytvoří pole `employee` objekty a hledá několik identifikátor a mzda hodnoty.  
  
 V příkladu se používá `choice` objektu k výběru mezi v následujících případech:  
  
1.  Zaměstnanec, který má zadaný identifikátor existuje.  
  
2.  Zaměstnanec, který má zadaný mzda existuje.  
  
3.  Žádný zaměstnanec, který má zadaný identifikátor nebo mzda existuje.  
  
 Pro první dva případy v příkladu se používá [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objekt pro uložení identifikátor a druhý `single_assignment` objekt pro uložení plat. V příkladu se používá `join` objekt třetí případu. `join` Objekt se skládá ze dvou Další `single_assignment` objekty, jeden pro případ, kde existuje žádný zaměstnanec, který má zadaný identifikátor a jeden pro případ, kdy žádný zaměstnanec, který má zadaný mzda existuje. `join` Objekt odešle zprávu, když každý ze členů přijme zprávu o. V tomto příkladu `join` objekt pošle, když žádný zaměstnanec, který má zadaný identifikátor nebo mzda existuje.  
  
 V příkladu se používá [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekt, který chcete paralelní spuštění obou algoritmů vyhledávání. Každý úkol vyhledávání zapíše do jednoho z `single_assignment` objekty, které se označují, zda daný zaměstnanec existuje. V příkladu se používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce získat index první vyrovnávací paměť, která obsahuje zprávu a `switch` bloku tisknout výsledek.  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Employee with id 14758 has salary 27780.00.  
Employee with salary 29150.00 has id 84345.  
Employee with id 61935 has salary 29905.00.  
No employee has id 899 or salary 31223.00.  
```  
  
 Tento příklad používá [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) pomocné funkce pro vytvoření `choice` objekty a [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) pomocné funkce pro vytvoření `join` objekty.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `find-employee.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc najít employee.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)   
 [Třída Choice](../../parallel/concrt/reference/choice-class.md)   
 [join – třída](../../parallel/concrt/reference/join-class.md)
