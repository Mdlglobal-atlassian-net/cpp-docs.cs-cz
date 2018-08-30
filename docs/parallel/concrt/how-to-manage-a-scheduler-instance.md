---
title: 'Postupy: Správa Instance plánovače | Dokumentace Microsoftu'
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
ms.openlocfilehash: 20730eb275dd2dd08f7ed7112b42ff1befa8e225
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222754"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Postupy: Správa instance plánovače
Instance plánovače umožňují specifické zásady plánování přidružit různé druhy úloh. Toto téma obsahuje dvě základní příklady ukazují, jak vytvořit a Správa instance plánovače.  
  
 Příklady vytvoření plánovače, které používají výchozí plánovač zásady. Pro příklad, který vytvoří plánovače, která používá vlastní zásady, najdete v článku [postupy: určení specifické zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Správa instance plánovače v aplikaci  
  
1.  Vytvoření [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objekt, který obsahuje zásady hodnoty plánovači používat.  
  

2.  Volání [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metoda nebo [concurrency::Scheduler::Create](reference/scheduler-class.md#create) metodu pro vytvoření instance plánovače.  
  
     Pokud používáte `Scheduler::Create` metody, volání [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metodu, když budete chtít Plánovač přidružit aktuálního kontextu.  
  
3.  Volání [funkce CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa) funkci, která vytvoří popisovač pro objekt nesignálového, automatické obnovení události.  
  
4.  Předat popisovač objektu události, který jste právě vytvořili, [concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) metoda nebo [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metoda. To zaregistruje událost bude nastaven při zničení plánovače.  
  
5.  Provádění úkolů, které chcete, aby aktuální scheduler k plánování.  
  
6.  Volání [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metodu detach aktuálního plánovače a obnovit předchozí Plánovač, jako je aktuální.  
  
     Pokud používáte `Scheduler::Create` metody, volání [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metoda se sníží počet odkazů `Scheduler` objektu.  
  
7.  Popisovač předat událost, abyste [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) funkce počkat, aby vypnout.  
  
8.  Volání [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211) funkce zavřít popisovač objektu události.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje dva způsoby, jak Správa instance plánovače. Každý nejprve příkladu je výchozím plánovačem provést úlohu, která vytiskne jedinečný identifikátor aktuálního plánovače. Každý příklad provést stejnou úlohu znovu použije instance plánovače. A konečně každý příklad obnoví výchozí plánovač jako aktuální a provede úkol ještě jednou.  
  
 V prvním příkladu se používá [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) třída pro vytvoření instance plánovače a přidružte jej k aktuálním kontextu. V druhém příkladu se používá [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) třídy provádějí stejné úkoly. Obvykle `CurrentScheduler` třída se používá pro práci s aktuálního plánovače. Druhý příklad, který používá `Scheduler` třídy, je užitečné, pokud chcete zajistit kontrolu, když Plánovač souvisí s aktuálním kontextu nebo pokud chcete přiřadit konkrétní plánovači s konkrétními úlohami.  
  
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
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `scheduler-instance.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.  
  
 **cl.exe/EHsc scheduler-instance.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Instance plánovače](../../parallel/concrt/scheduler-instances.md)   
 [Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

