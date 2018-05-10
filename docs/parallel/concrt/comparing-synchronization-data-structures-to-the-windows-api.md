---
title: Porovnávání synchronizačních datových struktur rozhraním API systému Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d1470911b13243a7c8b3befc627801368e89f04
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Porovnávání synchronizačních datových struktur s rozhraním API systému Windows
Toto téma porovnává chování synchronizační datové struktury, které jsou poskytovány Concurrency Runtime k protokolům poskytovaným rozhraní API systému Windows.  
  
 Synchronizační datové struktury, které jsou poskytovány Concurrency Runtime podle *spolupráce model vláken*. Ve spolupráci model vláken synchronizace primitiv explicitně yield jejich zpracování prostředků do jiné vlákno. Tím se liší od *preemptivní model vláken*, kde jsou zdroje zpracování přeneseny na jiná vlákna řízení scheduler nebo operačního systému.  
  
## <a name="criticalsection"></a>critical_section  
 [Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) třída podobá Windows `CRITICAL_SECTION` struktury, protože je možné použít pouze vlákny jeden proces. Další informace o kritické oddíly v rozhraní API systému Windows najdete v tématu [důležité části objekty](http://msdn.microsoft.com/library/windows/desktop/ms682530).  
  
## <a name="readerwriterlock"></a>reader_writer_lock  
 [Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) třída podobá zámky tenký čtečky/zápis (SRW) systému Windows. Následující tabulka vysvětluje podobnosti a rozdíly.  
  
|Funkce|`reader_writer_lock`|SRW zámku|  
|-------------|--------------------------|--------------|  
|Vícenásobně není přístupné|Ano|Ano|  
|Můžete zvýšit úroveň čtečku Writer (podpora upgradu)|Ne|Ne|  
|Můžete snížit úroveň zapisovač pro čtečku (podpora přechod na starší verzi)|Ne|Ne|  
|Zápis předvoleb zámku|Ano|Ne|  
|FIFO přístup k zapisovače|Ano|Ne|  
  
 Další informace o SRW zámky najdete v tématu [zámky tenký Reader/Writer (SRW)](http://msdn.microsoft.com/library/windows/desktop/aa904937) v sadě SDK pro platformu.  
  
## <a name="event"></a>event  
 [Concurrency::event](../../parallel/concrt/reference/event-class.md) třída podobá nepojmenované, Ruční vynulování události systému Windows. Však `event` objekt chová spolupráce při, zatímco ho preventivně chová událost systému Windows. Další informace o události systému Windows najdete v tématu [objektů událostí](http://msdn.microsoft.com/library/windows/desktop/ms682655).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Abyste lépe pochopili rozdíl mezi `event` třídy a události systému Windows, podívejte se na následující příklad. Tento příklad umožňuje vytvořit maximálně dvou souběžných úloh a poté volání dva podobné funkce, které používají Plánovač `event` třídy a Ruční vynulování událost systému Windows. Jednotlivé funkce nejprve vytvoří několik úloh, které čekat na sdílené událost, která má být signál. Jednotlivé funkce pak vypočítá na spuštěné úlohy a pak dá signál události. Jednotlivé funkce pak čeká signalizovaného událost.  
  
### <a name="code"></a>Kód  
 [!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Cooperative event:  
    Context 0: waiting on an event.  
    Context 1: waiting on an event.  
    Context 2: waiting on an event.  
    Context 3: waiting on an event.  
    Context 4: waiting on an event.  
    Setting the event.  
    Context 5: received the event.  
    Context 6: received the event.  
    Context 7: received the event.  
    Context 8: received the event.  
    Context 9: received the event.  
Windows event:  
    Context 10: waiting on an event.  
    Context 11: waiting on an event.  
    Setting the event.  
    Context 12: received the event.  
    Context 14: waiting on an event.  
    Context 15: received the event.  
    Context 16: waiting on an event.  
    Context 17: received the event.  
    Context 18: waiting on an event.  
    Context 19: received the event.  
    Context 13: received the event.  
```  
  
 Protože `event` třída chová spolupráce při, Plánovač můžete znovu přidělte zdroje zpracování na jiný kontext, když událost čeká na signalizovaného stavu. Proto další práci provádí na verzi, která používá `event` třídy. Ve verzi, která používá události systému Windows musí každý úkol čekání zadejte signalizovaného stavu před spuštěním další úlohy.  
  
 Další informace o úlohách najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Viz také  
 [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)
