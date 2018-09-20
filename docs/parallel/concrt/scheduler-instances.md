---
title: Instance plánovače | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc11888c3f655572bbdf33a5238e07f8ef99ba90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375651"
---
# <a name="scheduler-instances"></a>Instance plánovače

Tento dokument popisuje roli instance plánovače v Concurrency Runtime a jak používat [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) a [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) tříd pro vytvoření a Správa instance plánovače. Instance plánovače jsou užitečné, pokud chcete přidružit explicitní zásady plánování určité druhy úloh. Můžete například vytvořit jednu instanci plánovač spustit některé úlohy důležitostí vlákna se zvýšenými oprávněními a používají výchozí plánovač spustit další úkoly vláknu s normální prioritou.

> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

##  <a name="top"></a> Oddíly

- [Currentscheduler – třídy a Plánovač](#classes)

- [Vytvoření Instance plánovače](#creating)

- [Správa životního cyklu Instance plánovače](#managing)

- [Metody a funkce](#features)

- [Příklad](#example)

##  <a name="classes"></a> Currentscheduler – třídy a Plánovač

Plánovač úloh umožňuje aplikacím používat jeden nebo více *instance plánovače* na plánování práce. [Concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) třída představuje instance plánovače a zapouzdřuje funkce, které se vztahují k plánování úloh.

Podproces, který je připojen k plánovače se označuje jako *kontextu spuštění*, nebo jen *kontextu*. V každém okamžiku může být aktivní v aktuálním kontextu jeden plánovače. Aktivní Plánovač se také označuje jako *aktuálního plánovače*. Modul Concurrency Runtime používá [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) třídy pro zajištění přístupu k aktuálního plánovače. Pro jeden kontext aktuálního plánovače může lišit od aktuálního plánovače pro jiný kontext. Modul runtime neposkytuje úrovni procesu reprezentaci aktuálního plánovače.

Obvykle `CurrentScheduler` třída se používá pro přístup k aktuálního plánovače. `Scheduler` Třídy je užitečné, když je potřeba spravovat plánovače, která není aktuální.

Následující části popisují postup vytvoření a Správa instance plánovače. Kompletní příklad, který ilustruje tyto úkoly, naleznete v tématu [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

[[Horní](#top)]

##  <a name="creating"></a> Vytvoření Instance plánovače

Existují tyto tři způsoby, jak vytvořit `Scheduler` objektu:

- Pokud neexistuje žádný Plánovač, modul runtime vytvoří výchozí plánovače za vás při použití funkce modulu runtime, například paralelního algoritmu, k provedení práce. Výchozím plánovačem se změní aktuální Plánovač pro kontext, který se spustí paralelní práci.

- [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metoda vytvoří `Scheduler` objekt, který používá specifické zásady a přidruží tomto plánovači aktuálního kontextu.

- [Concurrency::Scheduler::Create](reference/scheduler-class.md#create) metoda vytvoří `Scheduler` objekt, který používá určité zásady, ale nepřidruží k aktuálním kontextu.

Povolení vytvoření plánovače výchozí modul runtime umožňuje všechny souběžných úloh sdílet stejnou plánovače. Obvykle, funkce, která je poskytována [knihovny Ppl](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) slouží k provádění paralelní práci. Proto nemáte pracovat přímo s plánovači řídit její zásady nebo doba života. Při použití PPL nebo knihovna agentů, modul runtime vytvoří výchozí plánovač, pokud neexistuje a díky tomu pro každý kontext aktuálního plánovače. Při vytvoření plánovače a nastavte ji jako aktuální Plánovač, modul runtime používá tento scheduler k plánování úloh. Vytvoření instance plánovače další jenom v případě, že budete vyžadovat konkrétní zásady plánování. Další informace o zásadách, které jsou spojeny s plánovače, naleznete v tématu [zásady plánovače](../../parallel/concrt/scheduler-policies.md).

[[Horní](#top)]

##  <a name="managing"></a> Správa životního cyklu Instance plánovače

Modul runtime používá mechanismus pro počítání odkazů k řízení životnosti `Scheduler` objekty.

Při použití `CurrentScheduler::Create` metoda nebo `Scheduler::Create` metodu pro vytvoření `Scheduler` objektu, modul runtime nastaví na jednu počáteční referenčního počtu tomto plánovači. Modul runtime zvýší počet odkazů při volání [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metody. `Scheduler::Attach` Metoda přidruží `Scheduler` společně s aktuálním kontextu. Díky tomu aktuálního plánovače. Při volání `CurrentScheduler::Create` vytvoří modul runtime obě metody `Scheduler` objektu a připojí ho k aktuální kontext (a nastaví počet odkazů na jeden). Můžete také použít [concurrency::Scheduler::Reference](reference/scheduler-class.md#reference) metoda se zvýší počet odkazů `Scheduler` objektu.

Runtime sníží počet referenční při volání [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metoda odpojit aktuálního plánovače nebo volání [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metoda. Když počet odkazů dosáhne nuly, odstraní modul runtime `Scheduler` objekt za všechny plánované úlohy dokončení. Spuštěná úloha může zvýšit počet odkazů z aktuálního plánovače. Proto pokud počet odkazů dosáhne nuly a zvýší počet odkazů úlohy, modul runtime nezničí `Scheduler` objektu, dokud počet odkazů dosáhne znovu nula a dokončení všech úkolů.

Modul runtime udržuje interní zásobníku `Scheduler` objekty pro každý kontext. Při volání `Scheduler::Attach` nebo `CurrentScheduler::Create` metody, modul runtime nabídek, které nebyly `Scheduler` objektu do zásobníku pro aktuální kontext. Díky tomu aktuálního plánovače. Při volání `CurrentScheduler::Detach`, modul runtime vyjme ze zásobníku pro aktuální kontext aktuálního plánovače a nastaví předchozímu jako aktuálního plánovače.

Modul runtime poskytuje několik způsobů, jak spravovat dobu života instance plánovače. V následující tabulce jsou uvedeny odpovídající metodu, která uvolní nebo odpojí plánovače z aktuálního kontextu pro každou metodu, která vytvoří a připojí plánovače na aktuální kontext.

|Vytvořit nebo připojit – metoda|Cesty k vydaným nebo detach – metoda|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

Volání nevhodný vydání nebo odpojit metoda vytvoří neurčené chování v modulu runtime.

Při použití funkce, například PPL, který způsobí, že modul runtime k vytvoření výchozího plánovače za vás, uvolnit nebo odpojit tento plánovač. Modul runtime spravuje životnost libovolné Plánovač, který vytvoří.

Vzhledem k tomu, že modul runtime nezničí `Scheduler` objekt před všechny úlohy nedokončí, můžete použít [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metoda nebo [concurrency::CurrentScheduler:: Registershutdownevent –](reference/currentscheduler-class.md#registershutdownevent) metodu pro příjem oznámení při `Scheduler` objekt zničen. To je užitečné, když každý úkol, který je naplánován podle musíte počkat `Scheduler` objektu na dokončení.

[[Horní](#top)]

##  <a name="features"></a> Metody a funkce

Tento oddíl shrnuje důležité metody `CurrentScheduler` a `Scheduler` třídy.

Představte si, že `CurrentScheduler` třídy jako pomůcka pro vytvoření plánovače pro použití v aktuálním kontextu. `Scheduler` Třída umožňuje řídit, která patří do jiného kontextu plánovače.

V následující tabulce jsou uvedeny důležité metody, které jsou definovány `CurrentScheduler` třídy.

|Metoda|Popis|
|------------|-----------------|
|[Vytvoření](reference/currentscheduler-class.md#create)|Vytvoří `Scheduler` objekt, který používá určené zásadě a přidruží ji k aktuálním kontextu.|
|[získat](reference/currentscheduler-class.md#get)|Načte ukazatel `Scheduler` objekt, který je přidružený k aktuální kontext. Tato metoda se nezvyšuje počet odkazů `Scheduler` objektu.|
|[Detach](reference/currentscheduler-class.md#detach)|Odpojí aktuální Plánovač z aktuálního kontextu a nastaví předchozímu jako aktuálního plánovače.|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|Zaregistruje událost, která modul runtime nastaví při zničení aktuálního plánovače.|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|Vytvoří [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objektu v aktuálního plánovače.|
|[Scheduletask –](reference/currentscheduler-class.md#scheduletask)|Lehký úkol přidá do plánování fronty aktuálního plánovače.|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|Načte kopii zásad, který je přidružený aktuální plánovač.|

V následující tabulce jsou uvedeny důležité metody, které jsou definovány `Scheduler` třídy.

|Metoda|Popis|
|------------|-----------------|
|[Vytvoření](reference/scheduler-class.md#create)|Vytvoří `Scheduler` objekt, který používá zadanou zásadu.|
|[Attach](reference/scheduler-class.md#attach)|Přidruží `Scheduler` společně s aktuálním kontextu.|
|[Referenční informace](reference/scheduler-class.md#reference)|Zvýší čítač odkaz `Scheduler` objektu.|
|[Vydaná verze](reference/scheduler-class.md#release)|Dekrementuje čítače odkaz `Scheduler` objektu.|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|Zaregistruje událost, která modul runtime nastaví, kdy `Scheduler` objekt zničen.|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|Vytvoří [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekt `Scheduler` objektu.|
|[Scheduletask –](reference/scheduler-class.md#scheduletask)|Naplánuje lehký úkol z `Scheduler` objektu.|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|Načte kopii zásad, který je přidružen `Scheduler` objektu.|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Nastavit zásady pro modul runtime pro použití při vytváření výchozím plánovačem.|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Obnoví výchozí zásady ten, který byl aktivní před voláním `SetDefaultSchedulerPolicy`. Pokud je výchozím plánovačem vytvořené po tomto volání, modul runtime používá výchozí nastavení zásady k vytvoření plánovače.|

[[Horní](#top)]

##  <a name="example"></a> Příklad

Základní příklady vytvoření a Správa instance plánovače, najdete v článku [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br/>
[Skupiny plánů](../../parallel/concrt/schedule-groups.md)

