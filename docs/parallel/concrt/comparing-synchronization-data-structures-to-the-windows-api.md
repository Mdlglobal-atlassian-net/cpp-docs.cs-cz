---
title: Porovnávání synchronizačních datových struktur s Windows rozhraní API | Dokumentace Microsoftu
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
ms.openlocfilehash: ff827c326f331acae4d16381856ad4df01550524
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447047"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Porovnávání synchronizačních datových struktur s rozhraním API systému Windows

Toto téma srovnává chování synchronizačních datových struktur, které jsou k dispozici v modulu Runtime souběžnosti do těch, které poskytuje rozhraní API Windows.

Synchronizační datové struktury, které jsou k dispozici v modulu Runtime souběžnosti, postupujte *kooperativní model vláken*. V spolupráce modelu vláken synchronizací primitiv explicitně yield jejich zpracování prostředků jiných vláken. Tím se liší od *preemptive model vláken*, kde jsou přeneseny prostředků pro zpracování pro ostatní vlákna řídící plánovače nebo operačního systému.

## <a name="criticalsection"></a>critical_section

[Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) třídy vypadá podobně jako Windows `CRITICAL_SECTION` struktury, protože ho lze použít pouze ve vláknech jeden proces. Další informace o kritické oddíly v rozhraní Windows API najdete v tématu [objektů kritických části](/windows/desktop/Sync/critical-section-objects).

## <a name="readerwriterlock"></a>reader_writer_lock

[Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) třídy se podobá zámky tenký čtení/zápis (SRW) pro Windows. Následující tabulka vysvětluje podobnosti a rozdíly.

|Funkce|`reader_writer_lock`|SRW zámku|
|-------------|--------------------------|--------------|
|Non-reentrant|Ano|Ano|
|Můžete zvýšit úroveň čtečku pro zápis (podporu upgradu)|Ne|Ne|
|Můžete snížit úroveň zapisovač pro čtečku (downgrade podpora)|Ne|Ne|
|Zámek zápisu předvoleb|Ano|Ne|
|FIFO přístup pro autory|Ano|Ne|

Další informace o zámky SRW najdete v tématu [tenký čtení/zápis (SRW) zámky](https://msdn.microsoft.com/library/windows/desktop/aa904937) v sadě SDK platformy.

## <a name="event"></a>event

[Concurrency::event](../../parallel/concrt/reference/event-class.md) třídy vypadá podobně jako nepojmenované, ruční obnovení události Windows. Nicméně `event` objekt chová kooperativně, zatímco události Windows chová preventivně. Další informace o událostech Windows najdete v tématu [objekty událostí](/windows/desktop/Sync/event-objects).

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Abyste lépe pochopili rozdíl mezi `event` třídy a události Windows, zvažte následující příklad. Tento příklad povolí, aby vytvořit maximálně dvou souběžných úloh a poté zavolá dvě podobné funkce, které používají `event` třídy a je ruční obnovení události Windows. Každá funkce nejprve vytvoří několik úloh, které čekat sdílené signálování události. Každá funkce potom provede na spuštěné úkoly a pak signalizuje událost. Každá funkce pak čeká signalizovaného událost.

### <a name="code"></a>Kód

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující ukázkový výstup:

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

Vzhledem k tomu, `event` třídy se chová kooperativně, Plánovač může přidělit jinému uživateli prostředků pro zpracování do jiného kontextu při události čeká vstupovat do signalizovaného stavu. Proto další práci provádí verzi, která se používá `event` třídy. Ve verzi, který využívá události Windows musí každý úkol čekání zadejte signalizovaného stavu před spuštěním další krok.

Další informace o úlohách najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Viz také

[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)
