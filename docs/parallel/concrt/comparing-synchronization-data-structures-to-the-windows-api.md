---
title: Porovnávání synchronizačních datových struktur s rozhraním API systému Windows
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510589"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Porovnávání synchronizačních datových struktur s rozhraním API systému Windows

Toto téma porovnává chování datových struktur synchronizace, které jsou poskytovány Concurrency Runtime, do těch, které poskytuje rozhraní API systému Windows.

Synchronizační datové struktury, které Concurrency Runtime poskytují, se řídí modelem pro *spolupráci*v družstvu. V modelu vláken v družstvu jsou primitivní primitivi explicitně vydávat prostředky zpracování do jiných vláken. To se liší od modelu nepracovních *vláken*, kde se zpracovávají prostředky, které řídí Scheduler nebo operační systém, a jsou přenášeny do jiných vláken.

## <a name="critical_section"></a>critical_section

Třída [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) se podobá struktuře systému Windows `CRITICAL_SECTION` , protože může být použita pouze vlákny jednoho procesu. Další informace o důležitých oddílech v rozhraní API systému Windows najdete v tématu [Důležité objekty oddílu](/windows/win32/Sync/critical-section-objects).

## <a name="reader_writer_lock"></a>reader_writer_lock

Třída [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) připomíná zámky Windows Slim Reader/Writer (SRW). V následující tabulce jsou vysvětleny podobnosti a rozdíly.

|Funkce|`reader_writer_lock`|SRW zámek|
|-------------|--------------------------|--------------|
|Netýká se opětovného zařazení|Ano|Ano|
|Může zvýšit úroveň čtecího modulu na zapisovač (podpora upgradu).|Ne|Ne|
|Může snížit úroveň zapisovače na čtenáře (podpora downgrade).|Ne|Ne|
|Zámek pro zápis a předvolby|Ano|Ne|
|Přístup FIFO k modulům pro zápis|Ano|Ne|

Další informace o SRW zámkech najdete v tématu zámky funkce [Slim Reader/Writer (SRW)](/windows/win32/sync/slim-reader-writer--srw--locks) v sadě SDK platformy.

## <a name="event"></a>event

Třída [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) se podobá nepojmenované události Windows ručního vynulování. `event` Objekt se ale chová v družstvě, zatímco se událost systému Windows chová bez přerušení. Další informace o událostech systému Windows naleznete v tématu [objekty událostí](/windows/win32/Sync/event-objects).

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Pro lepší pochopení rozdílu mezi `event` událostmi třídy a Windows zvažte následující příklad. Tento příklad umožňuje, aby Plánovač vytvořil nejvíce dvou souběžných úloh a pak volal dvě podobné funkce, které používají `event` třídu a událost ručního resetování Windows. Každá funkce nejprve vytvoří několik úloh, které čekají, až se na sdílenou událost zaznamená signál. Každá funkce následně vydává spuštěné úlohy a poté signalizuje událost. Každá funkce potom počká na událost signalizace.

### <a name="code"></a>Kód

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující vzorový výstup:

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

Vzhledem k `event` tomu, že se třída chová spolu, může Scheduler znovu přidělit prostředky zpracování jinému kontextu, když událost čeká na vstup do signalizace. Proto je více práce provedeno pomocí verze, která používá `event` třídu. V případě verze, která používá události systému Windows, musí každý čekající úkol před zahájením dalšího úkolu zadat signálový stav.

Další informace o úlohách najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Viz také:

[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)
