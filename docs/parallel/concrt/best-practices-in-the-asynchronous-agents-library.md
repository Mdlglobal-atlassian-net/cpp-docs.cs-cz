---
title: Osvědčené postupy v knihovně asynchronních agentů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e70b4004b24b04470e1fff280869887bbba74cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412740"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Osvědčené postupy v knihovně asynchronních agentů

Tento dokument popisuje, jak efektivně využívat asynchronní knihovnou agentů. Knihovna agentů povýší základě objektů actor programovací model a zprávy v procesu předávání pro hrubých toku dat a paralelní zpracování úloh.

Další informace o knihovna agentů najdete v tématu [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md).

##  <a name="top"></a> Oddíly

Tento dokument obsahuje následující části:

- [Izolace stavů pomocí agentů](#isolation)

- [Pomocí mechanismu omezování můžete omezit počet zpráv v datovém kanálu](#throttling)

- [Neprovádějte detailní operace v datovém kanálu](#fine-grained)

- [Nepředávejte datových částí velkých zpráv podle hodnoty](#large-payloads)

- [Použijte ukazatele shared_ptr v Data sítě při vlastnictví je definováno](#ownership)

##  <a name="isolation"></a> Izolace stavů pomocí agentů

Knihovna agentů poskytuje alternativy k sdíleného stavu tím, že umožňuje připojit izolované součásti přes asynchronní mechanismus předávání zpráv. Asynchronní agenti jsou nejužitečnější oddělovaly jejich vnitřní stav z jiných komponent. Prostřednictvím izolování stavu, více komponent neplní obvykle nad sdílenými daty. Stav izolace můžete povolit škálování, protože snižuje kolize na sdílené paměti vaší aplikace. Stav izolace také snižuje riziko zablokování a závodu podmínky komponenty nemají k synchronizaci přístupu k sdíleným datům.

Obvykle izolovat tak, že datových členů ve stavu agenta `private` nebo `protected` části třídy agenta a pomocí vyrovnávací paměti zpráv pro komunikaci změny stavu. Následující příklad ukazuje `basic_agent` třída, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `basic_agent` Třída používá dvě vyrovnávací paměti zpráv ke komunikaci s externí komponenty. Příchozí zprávy; obsahuje jednu vyrovnávací paměť zpráv Další vyrovnávací paměti zpráv obsahuje odchozí zprávy.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Kompletní příklady o tom, jak definovat a používat agenty, naleznete v tématu [návod: vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) a [návod: vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).

[[Horní](#top)]

##  <a name="throttling"></a> Pomocí mechanismu omezování můžete omezit počet zpráv v datovém kanálu

Mnoho typů vyrovnávací paměť zpráv, jako například [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), může obsahovat neomezený počet zpráv. Když autor zprávy rychleji, než příjemce může zpracovat tyto zprávy odešle zprávy do datového kanálu, můžete zadat aplikace stavu nedostatku paměti nebo na více instancí z důvodu nedostatku paměti. Mechanismu omezování, například semafor, můžete použít k omezení počtu zpráv, které jsou aktuálně aktivních v datovém kanálu.

V následujícím základním příkladu ukazuje, jak použít semafor omezit počet zpráv v datovém kanálu. Použití kanálu dat [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce pro simulaci operace, která trvá aspoň 100 milisekund. Vzhledem k tomu, že odesílatel zprávy vytvoří rychleji, než příjemce může zpracovávat zprávy, tento příklad definuje `semaphore` třídy povolit aplikace a omezit počet aktivních zpráv.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore` Omezuje objekt kanálu pro zpracování maximálně dvě zprávy ve stejnou dobu.

Výrobce v tomto příkladu odesílá relativně málo zprávy příjemci. Proto tento příklad neukazuje potenciální podmínku nedostatku paměti nebo na více instancí z důvodu nedostatku paměti. Tento mechanismus je však užitečný při datového kanálu obsahuje poměrně velké množství zpráv.

Další informace o tom, jak vytvořit Semaphore – třída, která se používá v tomto příkladu najdete v tématu [postupy: použití třídy kontextu pro implementaci semaforu kooperativní](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[[Horní](#top)]

##  <a name="fine-grained"></a> Neprovádějte detailní operace v datovém kanálu

Knihovna agentů je nejužitečnější při práci, kterou provádí datový kanál se poměrně hrubých. Například jedna součást aplikace může číst data ze souboru nebo připojení k síti a příležitostně data odeslat, k jiné součásti. Protokol, který knihovna agentů používá šíření zpráv způsobí, že mechanismus předávání zpráv s vyšší mírou režie než úloha paralelní konstrukce, které jsou k dispozici v [knihovny Ppl](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Proto zajistěte, aby práce, která se provádí pomocí datového kanálu dostatečně dlouhá, aby posun Tato dodatečná režie.

I datový kanál je nejúčinnější po hrubých jeho úkolů, každá fáze kanálu dat slouží k provádění více detailní operace PPL konstrukce, jako jsou skupiny úloh a paralelních algoritmů. Příklad hrubých data sítě, která používá dosáhnout jemně odstupňovaného paralelismu v každé fázi zpracování, naleznete v tématu [návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Horní](#top)]

##  <a name="large-payloads"></a> Nepředávejte datových částí velkých zpráv podle hodnoty

V některých případech se modul runtime vytvoří kopii všech zpráv, který předává z jednoho vyrovnávací paměť zpráv na jiné vyrovnávací paměť zpráv. Například [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) třída nabízí kopii všechny zprávy, které dostane na každý svůj cíl. Modul runtime také vytvoří kopii zprávy dat při použití funkce předávání zpráv, jako [concurrency::send](reference/concurrency-namespace-functions.md#send) a [concurrency::receive](reference/concurrency-namespace-functions.md#receive) pro zápis zpráv a čtení zpráv ze zprávy vyrovnávací paměť. Přestože tento mechanismus pomáhá eliminovat riziko souběžně zápisu do sdílených dat, může vést k paměti nízký výkon při relativně velké datovou část zprávy.

Můžete použít ukazatele nebo odkazy na zlepšení výkonu paměti při předávání zpráv, které mají velké datové části. Následující příklad porovnává předáním hodnoty velkých zpráv podle hodnoty k předání ukazatele na stejný typ zprávy. Příklad definuje dva typy agenta `producer` a `consumer`, které působí na `message_data` objekty. V příkladu porovná čas, který se vyžaduje pro výrobce k odesílání několika `message_data` příjemci na čas, který je požadován pro producenta agenta k odeslání několik ukazatelů na objekty `message_data` objekty příjemci.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

Verze, která používá ukazatele provádí lepší, protože eliminuje požadavek na modul runtime k vytvoření úplné kopie každé `message_data` objekt, který se předá od výrobce příjemci.

[[Horní](#top)]

##  <a name="ownership"></a> Použijte ukazatele shared_ptr v Data sítě při vlastnictví je definováno

Při odesílání zpráv ukazatelem prostřednictvím kanálu předávání zpráv nebo sítě obvykle přidělit paměť pro každou zprávu do přední části síť a uvolnit tuto paměť na konci sítě. Přestože tento mechanismus často funguje dobře, existují případy, ve které je obtížné nebo nebylo možné ji použít. Zvažte například případ, ve kterém datovou síť obsahuje více uzlů end. V takovém případě není žádné vymazat umístění k uvolnění paměti pro zprávy.

Chcete-li tento problém vyřešit, můžete použít mechanismus, například [std::shared_ptr](../../standard-library/shared-ptr-class.md), umožňující ukazatel na vlastnit více komponent. Při poslední `shared_ptr` objekt, který vlastní prostředek, zničen, prostředek je uvolněn také.

Následující příklad ukazuje, jak používat `shared_ptr` sdílet ukazatel hodnoty mezi několika vyrovnávací paměti zpráv. Příklad se připojuje [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objekt má tři [concurrency::call](../../parallel/concrt/reference/call-class.md) objekty. `overwrite_buffer` Třída nabízí zprávy pro každý svůj cíl. Protože existuje více vlastníkům dat na konci datovou síť, tento příklad používá `shared_ptr` můžete povolit každou `call` objekt sdílet vlastnictví zprávy.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

Tento příklad vytvoří následující ukázkový výstup:

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

