---
title: Prosté úlohy
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 19918cf73c2b5b03db895c4751b22b1666ce01de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346354"
---
# <a name="lightweight-tasks"></a>Prosté úlohy

Tento dokument popisuje využití jednoduché úlohy v modulu Runtime souběžnosti. A *lehký úkol* je úloha, kterou naplánujete přímo z `concurrency::Scheduler` nebo `concurrency::ScheduleGroup` objektu. Lehký úkol vypadá podobně jako funkce, které poskytují rozhraní Windows API [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkce. Prosté úlohy proto jsou užitečné při přizpůsobení stávajícího kódu pro použití funkce plánování modulu Runtime souběžnosti. Samotný modul Concurrency Runtime používá k plánování asynchronních agentů a zasílání zpráv mezi asynchronní bloky zpráv jednoduché úlohy.

> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

Prosté úlohy provést menší nároky na než asynchronní agenti a skupiny úloh. Například modul runtime neinformuje můžete po dokončení lehký úkol. Kromě toho modul runtime nepodporuje catch ani zpracovat výjimky, které jsou vyvolány z lehký úkol. Další informace o zpracování výjimek a jednoduché úlohy, naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Pro většinu úloh doporučujeme, že používáte více robustní funkce, jako jsou skupiny úloh a paralelních algoritmů protože umožňují snadněji rozdělit složité úlohy na ty informace o jednodušší. Další informace o skupinách úkolů najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelních algoritmech naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Chcete-li vytvořit lehký úkol, zavolejte [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), nebo [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) metody. Čekání na dokončení nenáročné úlohy, počkejte Plánovač nadřazené vypnout nebo pomocí mechanismu synchronizace, jako [concurrency::event](../../parallel/concrt/reference/event-class.md) objektu.

## <a name="example"></a>Příklad

Příklad, který ukazuje, jak přizpůsobit existující kód používal prostou úlohu, naleznete v tématu [názorný postup: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
