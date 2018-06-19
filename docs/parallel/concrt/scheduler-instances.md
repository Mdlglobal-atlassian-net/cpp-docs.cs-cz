---
title: Instance plánovače | Microsoft Docs
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
ms.openlocfilehash: 4f09a5708fd9140619eea60fb8e483c2e26165d1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693858"
---
# <a name="scheduler-instances"></a>Instance plánovače
Tento dokument popisuje roli instance plánovače v Concurrency Runtime a jak používat [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) a [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) třídy Vytvoření a Správa instance plánovače. Instance plánovače jsou užitečné, pokud chcete přidružit explicitní plánování zásady konkrétní typy úloh. Můžete například vytvořit jednu instanci plánovače spouštět některé úlohy prioritou zvýšenými vláken a používat výchozí plánovač při spouštění dalších úloh na normální vlákno prioritu.  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovač, a proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
##  <a name="top"></a> Oddíly  
  
-   [Plánovač a CurrentScheduler třídy](#classes)  
  
-   [Vytvoření Instance plánovače](#creating)  
  
-   [Správa životního cyklu instance plánovače](#managing)  
  
-   [Metody a funkce](#features)  
  
-   [Příklad](#example)  
  
##  <a name="classes"></a> Plánovač a CurrentScheduler třídy  
 Plánovač úloh umožňuje aplikacím používat jeden nebo více *instance plánovače* k plánování práce. [Concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) třída reprezentuje instance plánovače a zapouzdřuje funkce, které se vztahuje k plánování úloh.  
  
 Podproces, který je připojen k plánovače se označuje jako *kontext spuštění*, nebo jenom *kontextu*. Jeden scheduler můžou být aktivní v aktuálním kontextu kdykoli. Je také označován jako aktivní plánovače *aktuálního plánovače*. Používá Concurrency Runtime [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) třídy pro poskytnutí přístupu k aktuálního plánovače. Pro jeden kontextu aktuálního plánovače se může lišit od aktuálního plánovače pro jiný kontext. Modul runtime neposkytuje reprezentace aktuálního plánovače úrovni procesu.  
  
 Obvykle `CurrentScheduler` třída se používá pro přístup k aktuálního plánovače. `Scheduler` Třída je užitečná, když potřebujete spravovat Plánovač, který není aktuální.  
  
 Následující části popisují postup vytvoření a Správa instance plánovače. Úplný příklad, který znázorňuje tyto úkoly, najdete v části [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
 [[Horní](#top)]  
  
##  <a name="creating"></a> Vytvoření Instance plánovače  
 Existují tyto tři způsoby, jak vytvořit `Scheduler` objektu:  
  
-   Pokud žádné scheduler existuje, modul runtime vytvoří výchozí plánovače za vás při použití funkcionalita modulu runtime, například paralelní algoritmus pro práci. Výchozí plánovač stane aktuálního plánovače pro kontext, který iniciuje paralelní práce.  
  

-   [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) metoda vytvoří `Scheduler` objekt, který používá určité zásady a přidruží tento plánovač aktuálního kontextu.  
  
-   [Concurrency::Scheduler::Create](reference/scheduler-class.md#create) metoda vytvoří `Scheduler` objekt, který používá určité zásady, ale nespojuje s aktuálním kontextu.  

  
 Povolení modulu runtime vytvoření plánovače výchozí umožňuje všechny souběžné úlohy sdílet stejnou plánovače. Obvykle funkce, které poskytuje [Parallel Library vzory](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) se používá k provádění paralelní práce. Proto není nutné pracovat přímo s Plánovač k řízení jeho zásady nebo doba života. Při použití knihovně PPL nebo knihovna agentů, modul runtime vytvoří výchozí plánovač, pokud neexistuje a umožňuje aktuálního plánovače pro každý kontext. Při vytvoření plánovače a nastavte jej jako aktuálního plánovače, modul runtime používá tento plánovač plánování úloh. Vytvoření instance další plánovače jenom v případě, že budete potřebovat konkrétní zásady plánování. Další informace o zásadách, které jsou přidružené plánovače najdete v tématu [zásady plánovače](../../parallel/concrt/scheduler-policies.md).  
  
 [[Horní](#top)]  
  
##  <a name="managing"></a> Správa životního cyklu instance plánovače  
 Modul runtime používá mechanismus počítání odkaz k řízení životnost `Scheduler` objekty.  
  

 Při použití `CurrentScheduler::Create` metoda nebo `Scheduler::Create` metodu pro vytvoření `Scheduler` objektu modulu runtime nastaví odkaz na počáteční počet této scheduler na jeden. Modul runtime zvýší počet odkazů při volání [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) metoda. `Scheduler::Attach` Metoda partnerů `Scheduler` objekt spolu s aktuálním kontextu. Díky tomu aktuálního plánovače. Při volání `CurrentScheduler::Create` vytvoří modul runtime obě metody `Scheduler` objektu a připojí k aktuální kontext (a nastaví počet odkazů na jednu). Můžete také [concurrency::Scheduler::Reference](reference/scheduler-class.md#reference) metoda se zvýší počet odkazů `Scheduler` objektu.  
  
 Snižuje runtime odkaz na počet při volání [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) metoda odpojit aktuálního plánovače, nebo volejte [concurrency::Scheduler::Release](reference/scheduler-class.md#release) metoda. Pokud počet odkazů hodnota nula, zničí modul runtime `Scheduler` objekt za všechny naplánované úlohy dokončit. Spuštěná úloha může zvýšit počet odkazů aktuálního plánovače. Proto pokud počet odkazů hodnota nula, a úlohu zvýší počet odkazů, modul runtime nezničí `Scheduler` objektu, dokud počet odkazů opět dosáhne nula a dokončete všechny úlohy.  

  
 Modul runtime udržuje interní zásobník `Scheduler` objekty pro každý kontext. Při volání `Scheduler::Attach` nebo `CurrentScheduler::Create` metoda, modul runtime nabízených oznámení, která `Scheduler` objektu do zásobníku pro aktuální kontext. Díky tomu aktuálního plánovače. Při volání `CurrentScheduler::Detach`, modul runtime POP aktuálního plánovače v zásobníku pro aktuální kontext a nastaví předchozímu jako aktuálního plánovače.  
  
 Modul runtime poskytuje několik způsobů, jak spravovat dobu životnosti instance plánovače. Následující tabulka uvádí odpovídající metodu, která uvolní nebo odpojí Plánovač z aktuálního kontextu pro každou metodu, která vytvoří nebo připojí plánovače na aktuální kontext.  
  
|Vytvořit nebo attach – metoda|Verze nebo detach – metoda|  
|-----------------------------|------------------------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 Volání nevhodných verzi nebo odpojení metoda vytváří neurčené chování v modulu runtime.  
  
 Při použití funkce, například PPL, který způsobuje, že modul runtime pro vytvoření výchozí plánovače za vás, vydání nebo odpojit tento plánovače. Modul runtime spravuje životnost všechny plánovače, kterou vytvoří.  
  

 Vzhledem k tomu, že modul runtime nezničí `Scheduler` objekt před dokončení všech úloh, můžete použít [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) metoda nebo [concurrency::CurrentScheduler:: Registershutdownevent –](reference/currentscheduler-class.md#registershutdownevent) metoda pro příjem oznámení při `Scheduler` objekt zničena. To je užitečné, když je nutné počkat každý úkol, který je naplánováno podle `Scheduler` objekt, který chcete dokončit.  
  
 [[Horní](#top)]  
  
##  <a name="features"></a> Metody a funkce  
 Tento oddíl shrnuje důležité metody `CurrentScheduler` a `Scheduler` třídy.  
  
 Představte si, že `CurrentScheduler` třída jako pomocné rutiny pro vytvoření plánovače pro použití v aktuálním kontextu. `Scheduler` Třída umožňuje řídit plánovače, který patří do jiného kontextu.  
  
 V následující tabulce jsou uvedeny důležité metody, které jsou definovány `CurrentScheduler` třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Vytvoření](reference/currentscheduler-class.md#create)|Vytvoří `Scheduler` objekt, který se používá k určené zásadě a přidruží ji s aktuálním kontextu.|  
|[GET](reference/currentscheduler-class.md#get)|Načte ukazatel `Scheduler` objektu, která souvisí s aktuálním kontextu. Tato metoda se nezvyšuje počet odkazů `Scheduler` objektu.|  
|[Detach](reference/currentscheduler-class.md#detach)|Odpojí aktuální Plánovač z aktuálního kontextu a nastaví předchozímu jako aktuálního plánovače.|  
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|Zaregistruje událost, která nastaví modul runtime při zničena aktuálního plánovače.|  
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|Vytvoří [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekt v aktuálního plánovače.|  
|[Scheduletask –](reference/currentscheduler-class.md#scheduletask)|Prosté úlohy přidá do plánování frontu aktuálního plánovače.|  
|[Getpolicy –](reference/currentscheduler-class.md#getpolicy)|Načte kopii zásadami, které souvisí s aktuálního plánovače.|  
  
 V následující tabulce jsou uvedeny důležité metody, které jsou definovány `Scheduler` třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Vytvoření](reference/scheduler-class.md#create)|Vytvoří `Scheduler` objekt, který používá zadanou zásadu.|  
|[Attach](reference/scheduler-class.md#attach)|Přidruží `Scheduler` objekt spolu s aktuálním kontextu.|  
|[Referenční informace](reference/scheduler-class.md#reference)|Zvýší čítače odkaz z `Scheduler` objektu.|  
|[Vydaná verze](reference/scheduler-class.md#release)|Snižuje čítači, odkaz `Scheduler` objektu.|  
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|Zaregistruje událost, která nastaví modul runtime, kdy `Scheduler` objekt zničena.|  
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|Vytvoří [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekt v `Scheduler` objektu.|  
|[Scheduletask –](reference/scheduler-class.md#scheduletask)|Naplánuje úlohu lightweight z `Scheduler` objektu.|  
|[Getpolicy –](reference/scheduler-class.md#getpolicy)|Načte kopii zásad, který je přidružen `Scheduler` objektu.|  
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Nastavení zásad pro modul runtime pro použití při vytvoří výchozí plánovače.|  
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Obnoví výchozí zásady ten, který byl aktivní před voláním `SetDefaultSchedulerPolicy`. Pokud po toto volání se vytvoří výchozí plánovač, modul runtime používá výchozí nastavení zásady k vytvoření plánovače.|  

  
 [[Horní](#top)]  
  
##  <a name="example"></a> Příklad  
 Základní příklady způsobu vytvoření a Správa instance plánovače najdete v tématu [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Zásady plánovače](../../parallel/concrt/scheduler-policies.md)   
 [Skupiny plánů](../../parallel/concrt/schedule-groups.md)

