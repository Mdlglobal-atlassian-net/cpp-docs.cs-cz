---
title: 'Postupy: Správa instance plánovače'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: c7ec321eaf0960dc14b61bbd8fdc76b53a31f8c5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141717"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Postupy: Správa instance plánovače

Instance Scheduleru umožňují přidružit konkrétní zásady plánování k různým typům úloh. Toto téma obsahuje dva základní příklady, které ukazují, jak vytvořit a spravovat instanci plánovače.

V příkladech se vytvářejí schedulery, které používají výchozí zásady plánovače. Příklad vytvoření plánovače, který používá vlastní zásadu, naleznete v tématu [How to: zadat konkrétní zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>Správa instance plánovače v aplikaci

1. Vytvořte objekt [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) , který obsahuje hodnoty zásad, které má Plánovač používat.

1. Voláním metody [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) nebo metody [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) vytvořte instanci plánovače.

   Použijete-li metodu `Scheduler::Create`, zavolejte metodu [Concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) , pokud potřebujete přidružit Plánovač k aktuálnímu kontextu.

1. Voláním funkce [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw) vytvoříte popisovač objektu události automatického resetování, který není signálem signalizace.

1. Předejte popisovač do objektu události, který jste právě vytvořili, do metody [Concurrency:: CurrentScheduler:: RegisterShutdownEvent –](reference/currentscheduler-class.md#registershutdownevent) nebo metody [Concurrency:: Scheduler:: RegisterShutdownEvent –](reference/scheduler-class.md#registershutdownevent) . Tím se registruje událost, která se nastaví při zničení plánovače.

1. Proveďte úkoly, které má aktuální Plánovač naplánovat.

1. Zavolejte metodu [Concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach) , čímž se odpojí aktuální Plánovač a obnoví se předchozí Plánovač jako aktuální.

   Použijete-li metodu `Scheduler::Create`, zavolejte metodu [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) pro snížení počtu odkazů objektu `Scheduler`.

1. Předat popisovač události funkci [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) pro čekání na vypnutí plánovače.

1. Voláním funkce [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) zavřete popisovač objektu události.

## <a name="example"></a>Příklad

Následující kód ukazuje dva způsoby, jak spravovat instanci plánovače. Každý příklad nejprve používá výchozí Plánovač k provedení úkolu, který tiskne jedinečný identifikátor aktuálního plánovače. Každý příklad pak pomocí instance plánovače provede stejnou úlohu znovu. Nakonec každý příklad obnoví výchozí Plánovač jako aktuální a provede úlohu ještě jednou.

První příklad používá třídu [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) k vytvoření instance Scheduleru a k jejímu přidružení k aktuálnímu kontextu. Druhý příklad používá třídu [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) k provedení stejné úlohy. Třída `CurrentScheduler` se obvykle používá pro práci s aktuálním plánovačem. Druhý příklad, který používá třídu `Scheduler`, je užitečný v případě, že chcete řídit, kdy je Plánovač přidružen k aktuálnímu kontextu nebo když chcete přidružit konkrétní plánovače k určitým úkolům.

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

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `scheduler-instance.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Scheduler-instance. cpp**

## <a name="see-also"></a>Viz také

[Instance plánovače](../../parallel/concrt/scheduler-instances.md)<br/>
[Postupy: Určení specifických zásad plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
