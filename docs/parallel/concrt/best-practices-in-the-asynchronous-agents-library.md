---
title: "Osvědčené postupy v knihovně asynchronních agentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15e4b6aca6d9f00806a37a04ffb7c93008125b6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Osvědčené postupy v knihovně asynchronních agentů
Tento dokument popisuje, jak provádět efektivní použití asynchronní knihovna agentů. Knihovna agentů zvýší úroveň služby založené na objektu actor programovací model a zprávy v procesu předávání pro hrubý toku dat a paralelní zpracování úlohy.  
  
 Další informace o knihovně agentů najdete v tématu [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md).  
  
##  <a name="top"></a>Oddíly  
 Tento dokument obsahuje následující části:  
  
- [Pomocí agentů Isolate stavu](#isolation)  
  
- [Použití omezení mechanismus a omezit počet zpráv v datovém kanálu](#throttling)  
  
- [Neprovádějte podrobných pracovní v datovém kanálu](#fine-grained)  
  
- [Nepředávejte datových částí velké zpráva podle hodnoty](#large-payloads)  
  
- [Použití shared_ptr v datové sítě při vlastnictví je definován](#ownership)  
  
##  <a name="isolation"></a>Pomocí agentů Isolate stavu  
 Knihovna agentů poskytuje alternativy do sdíleného stavu tím, že umožňuje připojit izolované komponenty prostřednictvím asynchronní mechanismus předávání zpráv. Asynchronní agenti jsou co nejúčinnější, kdy budou izolovat jejich vnitřní stav z ostatních součástí. Prostřednictvím izolování stavu, více součástí, které není fungují obvykle na sdílená data. Stav izolace můžete povolit aplikaci škálovat, protože snižuje kolize na sdílené paměti. Stavu izolace také snižuje riziko zablokování a soupeření podmínky, protože komponenty nemusíte synchronizovat přístup ke sdíleným datům.  
  
 Obvykle tím, že se data členů v izolovat stavu agenta `private` nebo `protected` částech třídy agenta a pomocí vyrovnávacích pamětí zpráv pro komunikaci změny stavu. Následující příklad ukazuje `basic_agent` třída, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `basic_agent` Třída používá dva vyrovnávacích pamětí zpráv ke komunikaci s externích součástí. Příchozí zprávy; obsahuje jednu vyrovnávací paměti zpráv Další vyrovnávací paměti zpráv uchovává odchozí zprávy.  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 Dokončení příklady o tom, jak definice a používání agentů najdete v tématu [návod: vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) a [návod: vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).  
  
 [[Horní](#top)]  
  
##  <a name="throttling"></a>Použití omezení mechanismus a omezit počet zpráv v datovém kanálu  
 Mnoho typů vyrovnávací paměť zpráv, jako například [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), může pojmout neomezený počet zpráv. Když autor zprávy odesílá zprávy do kanálu data rychleji, než příjemce může zpracovat tyto zprávy, můžete zadat aplikace stavu nedostatku paměti nebo z důvodu nedostatku paměti. Omezení mechanismus, například semafor, můžete omezit počet zpráv, které jsou aktuálně aktivních v datovém kanálu.  
  
 Základní následující příklad ukazuje, jak pomocí semafor omezit počet zpráv v datovém kanálu. Data kanálu používá [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce k simulaci operace, která trvá nejméně 100 milisekund. Protože odesílatel vytváří zprávy rychleji, než příjemce může zpracovat tyto zprávy, tento příklad definuje `semaphore` třídy, které chcete povolit aplikace a omezit počet active zpráv.  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 `semaphore` Objekt omezuje kanál ke zpracování maximálně dvě zprávy ve stejnou dobu.  
  
 Proto, že v tomto příkladu odešle poměrně málo zprávy k příjemce. Tento příklad proto nepředvádí potenciální podmínku nedostatku paměti nebo z důvodu nedostatku paměti. Tento mechanismus je však užitečné, když datový kanál obsahuje relativně velký počet zpráv.  
  
 Další informace o tom, jak vytvořit semaphore – třída, která se používá v tomto příkladu najdete v tématu [postupy: použití třídy kontextu pro implementaci semaforu spolupráce](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
 [[Horní](#top)]  
  
##  <a name="fine-grained"></a>Neprovádějte podrobných pracovní v datovém kanálu  
 Knihovna agentů je nejvhodnější pro práci, kterou provádí datovém kanálu je docela hrubý. Jedna součást aplikace může například čtení dat ze souboru nebo připojení k síti a příležitostně odesílat data do jiné komponenty. Protokol, který používá knihovna agentů potřebný k šíření zprávy způsobí, že tento mechanismus předávání zpráv do mají další režii než paralelní konstrukce úloh, které jsou poskytovány [Parallel Library vzory](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Proto zkontrolujte, že je práce, které se provádí pomocí datovém kanálu dostatečně dlouhé, aby posun Tato dodatečná režie.  
  
 I když datový kanál je co nejúčinnější, pokud její úkoly hrubý, každá fáze v kanálu dat slouží k provádění více podrobných pracovní PPL konstrukce, jako je například skupin úloh a paralelní algoritmy. Příklad sítě hrubý data, která používá podrobných paralelismus v každé fázi zpracování naleznete v části [návod: vytváření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Horní](#top)]  
  
##  <a name="large-payloads"></a>Nepředávejte datových částí velké zpráva podle hodnoty  

 V některých případech modul runtime vytvoří kopii každé zprávy, který předává z jedné vyrovnávací paměti zpráv do jiné vyrovnávací paměti zpráv. Například [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) třída nabízí kopii každou zprávu, která obdrží pro každý z jeho cíle. Modul runtime také vytvoří kopii daty zprávy, při použití funkce předávání zpráv, jako [concurrency::send](reference/concurrency-namespace-functions.md#send) a [concurrency::receive](reference/concurrency-namespace-functions.md#receive) pro zápis zpráv do a čtení zpráv z zpráv vyrovnávací paměť. Přestože tento mechanismus pomáhá eliminovat riziko souběžně zápis do sdílených dat, může vést k paměti nízký výkon při relativně velké datové části zprávy.  
  
 Můžete použít ukazatele nebo odkazy ke zlepšení výkonu paměti při předání zprávy mají velké datové části. Následující příklad porovnává předávání velké zprávy hodnotou předávání ukazatele na stejný typ zprávy. V příkladu definuje dva typy agenta, `producer` a `consumer`, které fungují v `message_data` objekty. V příkladu porovná čas, který je vyžadován pro producent odeslat několik `message_data` objekty k příjemce na dobu, která je požadována pro agenta producent odeslat několik ukazatele na `message_data` objekty k příjemce.  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Using message_data...  
took 437ms.  
Using message_data*...  
took 47ms.  
```  
  
 Verze, která používá ukazatele provádí lépe, protože eliminuje požadavek na vytvoření úplné kopie modulu runtime každých `message_data` objekt, který předává od výrobce k příjemce.  
  
 [[Horní](#top)]  
  
##  <a name="ownership"></a>Použití shared_ptr v datové sítě při vlastnictví je definován  
 Při odesílání zpráv ukazatel prostřednictvím kanálu předávání zpráv nebo sítě obvykle přidělit paměť pro každou zprávu vpředu sítě a uvolnit paměť, že na konci sítě. I když tento mechanismus často funguje dobře, existují případy, ve které je obtížné nebo není možné ji použít. Představte si třeba tento případ, ve kterém datovou síť obsahuje více uzlů end. V takovém případě není žádná zrušte umístění pro uvolnění paměti pro zprávy.  
  
 Pokud chcete tento problém vyřešit, můžete použít mechanismus, například [std::shared_ptr](../../standard-library/shared-ptr-class.md), která umožňuje ukazatel na vlastnit více součástí. Když konečné `shared_ptr` zničena objektu, který vlastní prostředek, prostředek je také uvolněno.  
  
 Následující příklad ukazuje, jak používat `shared_ptr` sdílet hodnot ukazatele mezi několik vyrovnávacích pamětí zpráv. V příkladu se připojuje [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objekt, který má tři [concurrency::call](../../parallel/concrt/reference/call-class.md) objekty. `overwrite_buffer` Třída nabízí zprávy pro každý z jeho cíle. Protože nejsou k dispozici více vlastníky dat na konci datovou síť, tento příklad používá `shared_ptr` můžete povolit každou `call` objekt, který chcete sdílet vlastnictví zprávy.  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
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
 [Osvědčené postupy Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Osvědčené postupy v Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Obecné osvědčené postupy v Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

