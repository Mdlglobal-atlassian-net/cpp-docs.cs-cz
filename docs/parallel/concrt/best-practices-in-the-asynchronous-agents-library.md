---
title: Osvědčené postupy v knihovně asynchronních agentů
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 1cd6b54a014d35d17c732ed52f8529b05274585b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142099"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Osvědčené postupy v knihovně asynchronních agentů

Tento dokument popisuje, jak zajistit efektivní použití knihovny asynchronních agentů. Knihovna agentů propaguje model programování založený na objektech actor a předávání zpráv v rámci procesu pro hrubý úlohy toku dat a úloh.

Další informace o knihovně agentů najdete v tématu [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="top"></a>Řezů

Tento dokument obsahuje následující části:

- [Izolovat stav pomocí agentů](#isolation)

- [Omezení počtu zpráv v datovém kanálu pomocí mechanismu omezování](#throttling)

- [Neprovádějte jemně odstupňovanou práci v datovém kanálu](#fine-grained)

- [Nepředávejte velkou datovou část zprávy podle hodnoty](#large-payloads)

- [Použití shared_ptr v datové síti, když není definované vlastnictví](#ownership)

## <a name="isolation"></a>Izolovat stav pomocí agentů

Knihovna agentů poskytuje alternativy ke sdílenému stavu tím, že vám umožní připojit izolované komponenty prostřednictvím asynchronního mechanismu předávání zpráv. Asynchronní agenti jsou nejúčinnější, když izolují svůj vnitřní stav od ostatních komponent. Po izolování stavu nefungují pro sdílená data obvykle více komponent. Izolace stavu může povolit škálování vaší aplikace, protože snižuje kolize sdílené paměti. Izolace stavu také snižuje riziko zablokování a konfliktů časování, protože komponenty nemusí synchronizovat přístup ke sdíleným datům.

Stav se obvykle izoluje v agentovi tím, že uchovává datové členy v `private` nebo `protected` sekcích třídy agenta a pomocí vyrovnávací paměti zpráv pro komunikaci se změnami stavu. Následující příklad ukazuje třídu `basic_agent`, která je odvozena z [: concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). Třída `basic_agent` používá ke komunikaci s externími komponentami dvě vyrovnávací paměti zpráv. Jedna vyrovnávací paměť zpráv obsahuje příchozí zprávy; Další vyrovnávací paměť zpráv uchovává odchozí zprávy.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Kompletní příklady definování a používání agentů najdete v tématu [Návod: Vytvoření aplikace založené na agentech](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) a [Návod: Vytvoření agenta toku](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)dat.

[[Nahoře](#top)]

## <a name="throttling"></a>Omezení počtu zpráv v datovém kanálu pomocí mechanismu omezování

Mnoho typů vyrovnávací paměti zpráv, například [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), může obsahovat neomezený počet zpráv. Když producent zprávy pošle zprávy do datového kanálu rychleji, než příjemce může tyto zprávy zpracovat, může aplikace zadat stav s nízkou pamětí nebo mimo paměť. K omezení počtu zpráv, které jsou v datovém kanálu souběžně aktivní, můžete použít mechanismus omezování, například semafor.

Následující základní příklad ukazuje, jak použít semafor k omezení počtu zpráv v datovém kanálu. Datový kanál používá funkci [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) k simulaci operace, která trvá minimálně 100 milisekund. Protože odesilatel generuje zprávy rychleji, než příjemce může tyto zprávy zpracovat, tento příklad definuje třídu `semaphore`, která aplikaci umožní omezit počet aktivních zpráv.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

Objekt `semaphore` omezuje kanál tak, aby zpracovával současně dvě zprávy.

Producent v tomto příkladu pošle uživateli relativně několik zpráv. Proto tento příklad neukazuje potenciální stav pro nedostatek paměti nebo nedostatek paměti. Tento mechanismus je ale užitečný, pokud datový kanál obsahuje poměrně velký počet zpráv.

Další informace o tom, jak vytvořit třídu semaforu, která je použita v tomto příkladu, naleznete v tématu [How to: Use a Context a implementujte semafor pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[[Nahoře](#top)]

## <a name="fine-grained"></a>Neprovádějte jemně odstupňovanou práci v datovém kanálu

Knihovna agentů je nejužitečnější, když je práce prováděná datovým kanálem poměrně hrubá. Například jedna součást aplikace může číst data ze souboru nebo z připojení k síti a občas tato data odesílat do jiné součásti. Protokol, který knihovna agentů používá ke šíření zpráv, způsobí, že mechanismus předávání zpráv má větší režii než úkoly paralelní konstrukce, které jsou k dispozici v [knihovně paralelních vzorů](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Proto se ujistěte, že práce prováděná datovým kanálem je dostatečně dlouhá, aby se tato režie mohla kompenzovat.

I když je datový kanál nejúčinnější, když jsou jeho úkoly hrubé, jednotlivé fáze datového kanálu můžou pomocí PPL konstrukce, jako jsou skupiny úloh a paralelní algoritmy, provádět přesnější práci. Příklad hrubé sítě dat, která používá jemně odstupňované paralelismus v jednotlivých fázích zpracování, najdete v tématu [Návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Nahoře](#top)]

## <a name="large-payloads"></a>Nepředávejte velkou datovou část zprávy podle hodnoty

V některých případech modul runtime vytvoří kopii každé zprávy, která je předána z jedné vyrovnávací paměti zprávy do jiné vyrovnávací paměti zpráv. Například třída [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) nabízí kopii každé zprávy, kterou obdrží do každého z cílů. Modul runtime také vytvoří kopii dat zprávy, pokud používáte funkce pro předávání zpráv, například [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) a [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) pro zápis zpráv do a čtení zpráv z vyrovnávací paměti zprávy. I když tento mechanismus pomáhá eliminovat riziko souběžného zápisu do sdílených dat, může to vést k špatnému výkonu paměti, pokud je datová část zprávy poměrně velká.

Můžete použít ukazatele nebo odkazy na zlepšení výkonu paměti při předávání zpráv, které mají velkou datovou část. Následující příklad porovná předávání velkých zpráv podle hodnoty a předání ukazatelů na stejný typ zprávy. Příklad definuje dva typy agentů, `producer` a `consumer`, které fungují na `message_data`ch objektech. Příklad porovnává čas, který je požadován pro producenta odeslání několika `message_data` objektů příjemci do doby, kterou má agent producenta odeslat několik ukazatelů pro `message_data` objektů příjemci.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

Verze, která používá ukazatele, je lepší, protože eliminuje požadavek, aby modul runtime vytvořil úplnou kopii každého objektu `message_data`, který předává od producenta příjemci.

[[Nahoře](#top)]

## <a name="ownership"></a>Použití shared_ptr v datové síti, když není definované vlastnictví

Když odesíláte zprávy podle ukazatele prostřednictvím kanálu pro předávání zpráv nebo sítě, obvykle přidělíte paměť pro každou zprávu na začátku sítě a uvolníte tuto paměť na konci sítě. I když tento mechanismus často funguje dobře, existují případy, kdy je obtížné nebo není možné ho použít. Zvažte například případ, ve kterém datová síť obsahuje více koncových uzlů. V tomto případě není k dispozici žádné jasné umístění pro uvolnění paměti pro zprávy.

Chcete-li tento problém vyřešit, můžete použít mechanismus, například [std:: shared_ptr](../../standard-library/shared-ptr-class.md), který umožňuje ukazateli vlastnit více komponent. Pokud je konečný objekt `shared_ptr`, který vlastní prostředek, zničen, prostředek je uvolněn také.

Následující příklad ukazuje, jak použít `shared_ptr` ke sdílení hodnot ukazatelů mezi více vyrovnávacími pamětmi zpráv. V příkladu je připojen objekt [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) k třem objektům [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) . Třída `overwrite_buffer` nabízí zprávy pro každý z svých cílů. Vzhledem k tomu, že na konci datové sítě existuje více vlastníků dat, tento příklad používá `shared_ptr` k povolení sdílení vlastnictví zpráv u jednotlivých objektů `call`.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

Tento příklad vytvoří následující vzorový výstup:

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>Viz také

[Osvědčené postupy v Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[Postupy: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Osvědčené postupy v knihovně PPL (Parallel Patterns Library)](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
