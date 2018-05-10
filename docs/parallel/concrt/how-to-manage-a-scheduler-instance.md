---
title: 'Postupy: Správa Instance plánovače | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 699abcbc75dc4f0df40d07d26c0e6987d4711fe3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-manage-a-scheduler-instance"></a>Postupy: Správa instance plánovače
Instance plánovače umožňují přidružit konkrétní zásady plánování různé druhy zátěží. Toto téma obsahuje dva základní příklady, které ukazují, jak vytvořit a spravovat instance plánovače.  
  
 Příklady vytvoření plánovače, které používají výchozí zásady plánovače. Příklad, který vytvoří plánovače, která používá vlastní zásady, najdete v části [postup: Zadejte specifické zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Správa instance plánovače v aplikaci  
  
1.  Vytvoření [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objekt, který obsahuje zásady hodnoty pro Plánovač používat.  
  

2.  Volání [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metoda nebo [concurrency::Scheduler::Create](reference/scheduler-class.md#create) metodu pro vytvoření instance plánovače.  
  
     Pokud použijete `Scheduler::Create` metoda, volání [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metoda, pokud je potřeba přidružit Plánovač aktuálního kontextu.  
  
3.  Volání [funkce CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396) funkce vytvořit popisovač pro objekt-signál, automatické resetování událostí.  
  
4.  Popisovač předat objekt událostí, který jste právě vytvořili [concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) metoda nebo [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metoda. Takovém postupu zaregistruje událost, když Plánovač zničena.  
  
5.  Provádějí úlohy, které chcete aktuálního plánovače při plánování.  
  
6.  Volání [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metodu detach aktuálního plánovače a obnovit předchozí Plánovač jako stávající.  
  
     Pokud použijete `Scheduler::Create` metoda, volání [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metoda se sníží počet odkazů `Scheduler` objektu.  
  
7.  Předat popisovač události [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032) funkce čekat Plánovač a ukončí se.  
  
8.  Volání [funkce CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) funkce zavřít popisovač události objektu.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje dva způsoby, jak Správa instance plánovače. Každý příklad používá výchozí plánovač nejprve provést úlohu, která se vytiskne na jedinečný identifikátor aktuálního plánovače. Instance plánovače každý příklad pak používá k znovu provést stejný úkol. Nakonec každý příklad obnoví výchozí plánovač jako aktuální a provádí úkol ještě jednou.  
  
 V prvním příkladu používá [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) třída pro vytvoření instance plánovače a přidružte ji k aktuálním kontextu. Používá v druhém příkladu [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) třídy provést stejný úkol. Obvykle `CurrentScheduler` třída se používá pro práci s aktuálního plánovače. Druhého příkladu, který používá `Scheduler` třídy, je užitečné, pokud chcete řídit, kdy plánovač souvisí s aktuálním kontextu nebo když chcete přidružit konkrétní plánovače konkrétní úlohy.  
  
 [!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Using CurrentScheduler class...  
 
Current scheduler id: 0  
Creating and attaching scheduler...  
Current scheduler id: 1  
Detaching scheduler...  
Current scheduler id: 0  
 
Using Scheduler class...  
 
Current scheduler id: 0  
Creating scheduler...  
Attaching scheduler...  
Current scheduler id: 2  
Detaching scheduler...  
Current scheduler id: 0  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `scheduler-instance.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc scheduler-instance.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Instance plánovače](../../parallel/concrt/scheduler-instances.md)   
 [Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

