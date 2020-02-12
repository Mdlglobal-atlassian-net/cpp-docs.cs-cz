---
title: Instance plánovače
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: e9e9b8124254084ac30191d37d49f2ef72bd677e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142296"
---
# <a name="scheduler-instances"></a>Instance plánovače

Tento dokument popisuje roli instancí Scheduleru v Concurrency Runtime a způsob použití tříd [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) a [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) k vytváření a správě instancí plánovače. Instance plánovače jsou užitečné, pokud chcete přidružit explicitní zásady plánování ke konkrétním typům úloh. Můžete například vytvořit jednu instanci Scheduleru, která bude spouštět některé úlohy se zvýšenou prioritou, a použít výchozí Plánovač pro spouštění dalších úloh s normální prioritou vlákna.

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač, a proto není nutné ho v aplikaci vytvořit. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

## <a name="top"></a>Řezů

- [Třídy Scheduler a CurrentScheduler](#classes)

- [Vytvoření instance Scheduleru](#creating)

- [Správa životnosti instance Scheduleru](#managing)

- [Metody a funkce](#features)

- [Příklad](#example)

## <a name="classes"></a>Třídy Scheduler a CurrentScheduler

Plánovač úloh umožňuje aplikacím použít jednu nebo více *instancí plánovače* k naplánování práce. Třída [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) reprezentuje instanci Scheduleru a zapouzdřuje funkčnost související s plánováním úloh.

Vlákno, které je připojeno ke Scheduleru, je známé jako *kontext spuštění*nebo pouze *kontext*. Jeden Plánovač může být kdykoli aktivní v aktuálním kontextu. Aktivní Plánovač se také označuje jako *aktuální Plánovač*. Concurrency Runtime používá třídu [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) k poskytnutí přístupu k aktuálnímu plánovači. Aktuální Plánovač pro jeden kontext se může od aktuálního plánovače lišit pro jiný kontext. Modul runtime neposkytuje reprezentace na úrovni procesu aktuálního plánovače.

Třída `CurrentScheduler` se obvykle používá pro přístup k aktuálnímu plánovači. Třída `Scheduler` je užitečná v případě, že potřebujete spravovat Plánovač, který není aktuálním členem.

Následující části popisují, jak vytvořit a spravovat instanci plánovače. Úplný příklad, který znázorňuje tyto úkoly, naleznete v tématu [How to: manage a Scheduler instance](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

[[Nahoře](#top)]

## <a name="creating"></a>Vytvoření instance Scheduleru

Existují tři způsoby, jak vytvořit objekt `Scheduler`:

- Pokud žádný Plánovač neexistuje, modul runtime vytvoří výchozí Plánovač při použití běhových funkcí, například paralelního algoritmu k provedení práce. Výchozí Plánovač se bude aktuálním plánovačem pro kontext, který iniciuje paralelní práci.

- Metoda [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) vytvoří objekt `Scheduler`, který používá konkrétní zásadu a přidruží k tomuto plánovači aktuální kontext.

- Metoda [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) vytvoří objekt `Scheduler`, který používá konkrétní zásadu, ale nepřidruží ho k aktuálnímu kontextu.

Povolení modulu runtime pro vytvoření výchozího plánovače umožní všem souběžným úlohám sdílet stejný Plánovač. Obvykle se funkce, která je poskytována [knihovnou PPL (Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) ) nebo [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , používá k provedení paralelní práce. Proto není nutné pracovat přímo s plánovačem a řídit jeho zásady nebo dobu života. Použijete-li knihovnu PPL nebo agentů, modul runtime vytvoří výchozí Plánovač, pokud neexistuje, a provede ho pro každý kontext aktuálním plánovačem. Když vytvoříte Plánovač a nastavíte ho jako aktuální Plánovač, modul runtime použije tento Plánovač k plánování úloh. Další instance Scheduleru můžete vytvořit pouze v případě, že vyžadujete konkrétní zásadu plánování. Další informace o zásadách přidružených ke Scheduleru najdete v tématu [zásady plánovače](../../parallel/concrt/scheduler-policies.md).

[[Nahoře](#top)]

## <a name="managing"></a>Správa životnosti instance Scheduleru

Modul runtime používá mechanismus počítání odkazů k řízení životnosti `Scheduler` objektů.

Použijete-li metodu `CurrentScheduler::Create` nebo metodu `Scheduler::Create` k vytvoření objektu `Scheduler`, modul runtime nastaví počáteční počet odkazů tohoto plánovače na jeden. Modul runtime zvýší počet odkazů při volání metody [Concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) . Metoda `Scheduler::Attach` přidruží objekt `Scheduler` spolu s aktuálním kontextem. Tím se vytvoří aktuální Plánovač. Když zavoláte metodu `CurrentScheduler::Create`, modul runtime vytvoří objekt `Scheduler` a připojí ho k aktuálnímu kontextu (a nastaví počet odkazů na jeden). Můžete také použít metodu [Concurrency:: Scheduler:: Reference](reference/scheduler-class.md#reference) k zvýšení počtu odkazů objektu `Scheduler`.

Modul runtime sníží počet odkazů při volání metody [Concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach) pro odpojení aktuálního plánovače nebo volání metody [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) . Když počet odkazů dosáhne nuly, modul runtime zničí objekt `Scheduler` po dokončení všech naplánovaných úloh. Spuštěný úkol může zvýšit počet odkazů aktuálního plánovače. Proto pokud počet odkazů dosáhne nuly a úkol zvýší počet odkazů, modul runtime neodstraní objekt `Scheduler`, dokud počet odkazů opět nedosáhne hodnoty nula a všechny úkoly budou dokončeny.

Modul runtime udržuje interní zásobník `Scheduler` objektů pro každý kontext. Když zavoláte metodu `Scheduler::Attach` nebo `CurrentScheduler::Create`, modul runtime doručí, že `Scheduler` objekt do zásobníku pro aktuální kontext. Tím se vytvoří aktuální Plánovač. Když zavoláte `CurrentScheduler::Detach`, modul runtime pro aktuální kontext zobrazí aktuální Plánovač a nastaví předchozí Plánovač jako aktuální.

Modul runtime poskytuje několik způsobů, jak spravovat životnost instance Scheduleru. V následující tabulce je uvedena odpovídající metoda, která vydává nebo odpojuje Plánovač z aktuálního kontextu pro každou metodu, která vytváří nebo připojuje Plánovač k aktuálnímu kontextu.

|Vytvořit nebo připojit metodu|Metoda uvolnění nebo odpojení|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

Voláním metody uvolnění nebo odpojení vznikne nespecifikované chování v modulu runtime.

Když použijete funkci, například PPL, která způsobí, že modul runtime vytvoří výchozí Plánovač pro vás, neuvolní ani nepojí tohoto plánovače. Modul runtime spravuje životnost všech plánovačů, které vytvoří.

Vzhledem k tomu, že modul runtime nezničí objekt `Scheduler` před dokončením všech úloh, můžete použít metodu [Concurrency:: Scheduler:: RegisterShutdownEvent –](reference/scheduler-class.md#registershutdownevent) nebo metodu [Concurrency:: CurrentScheduler:: RegisterShutdownEvent –](reference/currentscheduler-class.md#registershutdownevent) pro příjem oznámení, když dojde k zničení objektu `Scheduler`. To je užitečné v případě, že je nutné počkat na dokončení všech úloh, které jsou naplánovány objektem `Scheduler`.

[[Nahoře](#top)]

## <a name="features"></a>Metody a funkce

Tato část shrnuje důležité metody `CurrentScheduler` a `Scheduler` třídy.

Třídu `CurrentScheduler` si můžete představit jako pomocníka pro vytvoření plánovače pro použití v aktuálním kontextu. Třída `Scheduler` umožňuje řídit Plánovač, který patří do jiného kontextu.

V následující tabulce jsou uvedeny důležité metody, které jsou definovány třídou `CurrentScheduler`.

|Metoda|Popis|
|------------|-----------------|
|[Vytvoření](reference/currentscheduler-class.md#create)|Vytvoří objekt `Scheduler`, který používá zadanou zásadu a přidruží ho k aktuálnímu kontextu.|
|[Get](reference/currentscheduler-class.md#get)|Načte ukazatel na objekt `Scheduler`, který je přidružen k aktuálnímu kontextu. Tato metoda nezvyšuje počet odkazů objektu `Scheduler`.|
|[Detach](reference/currentscheduler-class.md#detach)|Odpojí aktuálního plánovače od aktuálního kontextu a nastaví předchozí Plánovač jako aktuální.|
|[RegisterShutdownEvent –](reference/currentscheduler-class.md#registershutdownevent)|Registruje událost, kterou nastaví modul runtime při zničení aktuálního plánovače.|
|[CreateScheduleGroup –](reference/currentscheduler-class.md#createschedulegroup)|Vytvoří v aktuálním plánovači objekt [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) .|
|[ScheduleTask –](reference/currentscheduler-class.md#scheduletask)|Přidá odlehčený úkol do fronty plánování aktuálního plánovače.|
|[GetPolicy –](reference/currentscheduler-class.md#getpolicy)|Načte kopii zásady, která je přidružená k aktuálnímu plánovači.|

V následující tabulce jsou uvedeny důležité metody, které jsou definovány třídou `Scheduler`.

|Metoda|Popis|
|------------|-----------------|
|[Vytvoření](reference/scheduler-class.md#create)|Vytvoří objekt `Scheduler`, který používá zadanou zásadu.|
|[Attach](reference/scheduler-class.md#attach)|Přidruží objekt `Scheduler` spolu s aktuálním kontextem.|
|[Referenční informace](reference/scheduler-class.md#reference)|Zvýší referenční čítač objektu `Scheduler`.|
|[Vydaná verze](reference/scheduler-class.md#release)|Sníží referenční čítač objektu `Scheduler`.|
|[RegisterShutdownEvent –](reference/scheduler-class.md#registershutdownevent)|Registruje událost, která je nastavena za běhu, když je objekt `Scheduler` zničen.|
|[CreateScheduleGroup –](reference/scheduler-class.md#createschedulegroup)|Vytvoří objekt [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) v objektu `Scheduler`.|
|[ScheduleTask –](reference/scheduler-class.md#scheduletask)|Naplánuje odlehčenou úlohu z objektu `Scheduler`.|
|[GetPolicy –](reference/scheduler-class.md#getpolicy)|Načte kopii zásady, která je přidružená k objektu `Scheduler`.|
|[SetDefaultSchedulerPolicy –](reference/scheduler-class.md#setdefaultschedulerpolicy)|Nastaví zásady pro modul runtime, které se použijí při vytváření výchozího plánovače.|
|[Resetdefaultschedulerpolicy –](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Obnoví výchozí zásadu na tu, která byla aktivní před voláním `SetDefaultSchedulerPolicy`. Pokud se po tomto volání vytvoří výchozí Plánovač, modul runtime pro vytvoření plánovače použije výchozí nastavení zásad.|

[[Nahoře](#top)]

## <a name="example"></a>Případě

Základní příklady vytváření a správy instance Scheduleru najdete v tématu [How to: manage a Scheduler instance](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br/>
[Skupiny plánů](../../parallel/concrt/schedule-groups.md)
