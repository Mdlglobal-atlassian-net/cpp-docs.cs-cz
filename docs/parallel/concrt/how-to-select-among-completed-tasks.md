---
title: 'Postupy: výběr z dokončených úloh | Dokumentace Microsoftu'
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
ms.openlocfilehash: c458ab708af738d181bd720085c8cf533652d2a6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436049"
---
# <a name="how-to-select-among-completed-tasks"></a>Postupy: Výběr z dokončených úloh

Tento příklad ukazuje způsob použití [concurrency::choice](../../parallel/concrt/reference/choice-class.md) a [concurrency::join](../../parallel/concrt/reference/join-class.md) tříd vyberte první úkol k dokončení vyhledávacího algoritmu.

## <a name="example"></a>Příklad

Následující příklad provede dvě algoritmy hledání paralelně a vybere první algoritmus k dokončení. Tento příklad definuje `employee` typ, který obsahuje identifikační číslo a na plat pro zaměstnance. `find_employee` Funkce najde první zaměstnanec, který má zadaný identifikátor nebo zadaný salary. `find_employee` Funkce také řeší případ, kdy žádný zaměstnanec má zadaný identifikátor nebo salary. `wmain` Funkce vytvoří pole `employee` objekty a hledá v několika identifikátor a salary hodnot.

V příkladu se používá `choice` objektu k výběru mezi následujících případech:

1. Zaměstnanec, který má zadaný identifikátor existuje.

1. Zaměstnanec, který má zadaný salary existuje.

1. Neexistuje žádné zaměstnanec, který má zadaný identifikátor nebo platu.

Pro první dva případy v příkladu se používá [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objekt pro uložení identifikátor a jiné `single_assignment` objekt pro uložení mzdě. V příkladu se používá `join` objekt třetí případu. `join` Objektu se skládá ze dvou dalších `single_assignment` objekty, jeden pro případ, kdy neexistuje žádný zaměstnanec, který má zadaný identifikátor a jeden pro případ, kdy neexistuje žádné zaměstnanec, který má zadaný salary. `join` Objekt odešle zprávu, když každý z jejích členů obdrží zprávu. V tomto příkladu `join` odešle zprávu, když žádný zaměstnanec, který má zadaný identifikátor objektu nebo salary existuje.

V příkladu se používá [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu k paralelnímu spouštění algoritmy vyhledávání. Každý úkol hledání provede zápis do jednoho z `single_assignment` objektech k určení, zda existuje dané zaměstnance. V příkladu se používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce k získání indexu prvního vyrovnávací paměti, která obsahuje zprávy a `switch` bloku k vytištění výsledku.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

V tomto příkladu [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) pomocná funkce umožňující vytvoření `choice` objekty a [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) pomocná funkce umožňující vytvoření `join` objekty.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `find-employee.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc find-employee.cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[choice – třída](../../parallel/concrt/reference/choice-class.md)<br/>
[join – třída](../../parallel/concrt/reference/join-class.md)
