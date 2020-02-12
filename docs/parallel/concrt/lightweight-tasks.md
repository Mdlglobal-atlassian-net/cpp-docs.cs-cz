---
title: Prosté úlohy
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: be417052ffab19c1bc2d2ba6f35094f98e315812
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141855"
---
# <a name="lightweight-tasks"></a>Prosté úlohy

Tento dokument popisuje roli zjednodušených úloh v Concurrency Runtime. *Odlehčený úkol* je úkol, který naplánujete přímo z `concurrency::Scheduler` nebo `concurrency::ScheduleGroup` objektu. Nenáročná úloha se podobá funkci, kterou zadáte do funkce [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) rozhraní API systému Windows. Zjednodušené úlohy jsou proto užitečné při úpravách stávajícího kódu pro použití funkcí plánování Concurrency Runtime. Concurrency Runtime sám používá zjednodušené úlohy k plánování asynchronních agentů a posílání zpráv mezi asynchronními bloky zpráv.

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač, a proto není nutné ho v aplikaci vytvořit. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

Jednoduché úlohy mají méně režijních nákladů než Asynchronní agenti a skupiny úloh. Například modul runtime neoznamuje, že se dokončí odlehčená úloha. Kromě toho modul runtime nezachycuje ani nezpracovává výjimky, které jsou vyvolány z odlehčené úlohy. Další informace o zpracování výjimek a odlehčených úlohách naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Pro většinu úloh doporučujeme používat robustnější funkce, jako jsou skupiny úloh a paralelní algoritmy, protože umožňují snadněji rozdělit složité úlohy na další základní. Další informace o skupinách úloh najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelních algoritmech najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Chcete-li vytvořit odlehčenou úlohu, zavolejte metodu [Concurrency:: Schedule:: ScheduleTask –](reference/schedulegroup-class.md#scheduletask), [Concurrency:: CurrentScheduler:: ScheduleTask –](reference/currentscheduler-class.md#scheduletask)nebo [Concurrency:: Scheduler:: ScheduleTask –](reference/scheduler-class.md#scheduletask) . Chcete-li počkat na dokončení nenáročné úlohy, počkejte, než se nadřazený Plánovač vypne, nebo použijte synchronizační mechanismus, jako je objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) .

## <a name="example"></a>Příklad

Příklad, který ukazuje, jak upravit existující kód pro použití zjednodušené úlohy, naleznete v tématu [Návod: přizpůsobení stávajícího kódu pro použití zjednodušených úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
