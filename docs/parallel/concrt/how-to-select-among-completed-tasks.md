---
title: 'Postupy: Výběr z dokončených úloh'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 75ecac8dd0e8845401e3e287e8c95ea614055970
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142475"
---
# <a name="how-to-select-among-completed-tasks"></a>Postupy: Výběr z dokončených úloh

Tento příklad ukazuje, jak použít třídy [Concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) a [Concurrency:: JOIN](../../parallel/concrt/reference/join-class.md) k výběru prvního úkolu k dokončení vyhledávacího algoritmu.

## <a name="example"></a>Příklad

Následující příklad provádí dva vyhledávací algoritmy paralelně a vybere první algoritmus, který se má dokončit. Tento příklad definuje typ `employee`, který obsahuje číselný identifikátor a mzdu pro zaměstnance. Funkce `find_employee` vyhledá prvního zaměstnance, který má poskytnutý identifikátor nebo poskytnutý plat. Funkce `find_employee` také zpracovává případ, kdy žádný zaměstnanec nemá poskytnutý identifikátor nebo mzdu. Funkce `wmain` vytvoří pole objektů `employee` a vyhledá několik identifikátorů a hodnot mzdy.

V příkladu se používá objekt `choice` k výběru mezi následujícími případy:

1. Zaměstnanec, který má zadaný identifikátor, existuje.

1. Zaměstnanec, který má poskytnutý plat, existuje.

1. Neexistuje žádný zaměstnanec, který má zadaný identifikátor nebo mzdu.

V prvních dvou případech příklad používá objekt [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) k uložení identifikátoru a dalšího objektu `single_assignment` pro uložení mzdy. V příkladu se používá objekt `join` pro třetí případ. Objekt `join` se skládá ze dvou dalších objektů `single_assignment`, jeden pro případ, kdy neexistuje zaměstnanec, který má zadaný identifikátor, a druhý pro případ, kdy neexistuje zaměstnanec, který má poskytnutý plat. Objekt `join` odesílá zprávu, když každý z jejích členů obdrží zprávu. V tomto příkladu objekt `join` odesílá zprávu, pokud neexistuje žádný zaměstnanec, který má zadaný identifikátor nebo mzda.

V příkladu se používá objekt [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) k paralelnímu spuštění obou vyhledávacích algoritmů. Každá úloha vyhledávání zapisuje do jednoho z `single_assignment` objektů, aby označovala, zda daný zaměstnanec existuje. V příkladu se používá funkce [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) k získání indexu první vyrovnávací paměti, která obsahuje zprávu a `switch` blok pro vytištění výsledku.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

V tomto příkladu se používá pomocná funkce [Concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) k vytvoření objektů `choice` a pomocné funkce [concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) k vytvoření objektů `join`.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `find-employee.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Find-Employee. cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[choice – třída](../../parallel/concrt/reference/choice-class.md)<br/>
[join – třída](../../parallel/concrt/reference/join-class.md)
