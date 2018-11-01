---
title: Synchronizační datové struktury
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 8c91de87bb5d579916743051d06c15f6df6921bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495924"
---
# <a name="synchronization-data-structures"></a>Synchronizační datové struktury

Modul Concurrency Runtime obsahuje několik datových struktur, které umožňují synchronizaci přístupu ke sdíleným datům z více vláken. Tyto datové struktury jsou užitečné, pokud jste sdíleli data, která je upravit jen zřídka. Synchronizační objekt, například kritický oddíl, způsobí, že ostatní vlákna počkat, dokud sdíleného prostředku je k dispozici. Proto pokud takový objekt můžete používat k synchronizaci přístupu k datům, která se často používá, můžete ztratit škálovatelnost ve vaší aplikaci. [Knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) poskytuje [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídu, která umožňuje sdílení prostředků mezi několik vláken nebo úloh bez nutnosti synchronizace. Další informace o `combinable` najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).

##  <a name="top"></a> Oddíly

Toto téma popisuje následující typy asynchronních zpráv bloku podrobně:

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock a scoped_lock_read –](#scoped_lock)

- [event](#event)

##  <a name="critical_section"></a> critical_section –

[Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) třída reprezentuje kooperativní vzájemné vyloučení objektu, který poskytuje další úlohy místo je přerušený. Kritické oddíly jsou užitečné, pokud více vláken vyžadují výhradní pro čtení a zápis ke sdíleným datům.

`critical_section` Bez reentrant je třída. [Concurrency::critical_section::lock](reference/critical-section-class.md#lock) metoda vyvolá výjimku typu [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) Pokud je volána vláknem, který již vlastní zámek.

### <a name="methods-and-features"></a>Metody a funkce

V následující tabulce jsou uvedeny důležité metody, které jsou definovány `critical_section` třídy.

|Metoda|Popis|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Získá kritický oddíl. Volání kontextu blokuje, dokud získá zámek.|
|[try_lock](reference/critical-section-class.md#try_lock)|Pokusí se získat kritický oddíl, ale neblokuje.|
|[Odemknutí](reference/critical-section-class.md#unlock)|Uvolní kritický oddíl.|

[[Horní](#top)]

##  <a name="reader_writer_lock"></a> reader_writer_lock –

[Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) třída poskytuje operace bezpečné pro vlákna čtení a zápisu ke sdíleným datům. Zámky pro čtení/zápis použijte, pokud více vláken vyžadují souběžný přístup pro čtení ke sdíleným prostředkům, ale zřídka zapisovat do tohoto sdíleného prostředku. Tato třída poskytuje oprávnění k zápisu pouze jedno vlákno na objekt v každém okamžiku.

`reader_writer_lock` Mohou třídy provádět lepší, než `critical_section` třídy, protože `critical_section` objektu získá výhradní přístup ke sdíleným prostředkům, což zabrání souběžný přístup pro čtení.

Podobně jako `critical_section` třídy, `reader_writer_lock` třída reprezentuje kooperativní vzájemné vyloučení objektu, který poskytuje další úlohy místo je přerušený.

Pokud podproces, který musíte napsat ke sdíleným prostředkům získá zámek čtení/zápis, ostatní vlákna, které musí také přístup k prostředku jsou blokovány, dokud zapisovač, který uvolní zámek. `reader_writer_lock` Třídy je příkladem *zápisu předvoleb* zámek, což je zámek, který se odblokuje zapisovače čekání před odblokuje čtenáři čekání.

Podobně jako `critical_section` třídy, `reader_writer_lock` bez reentrant je třída. [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) a [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) metody vyvolat výjimku typu `improper_lock` Pokud jsou volány podproces, který již vlastní zámek.

> [!NOTE]
>  Vzhledem k tomu, `reader_writer_lock` bez reentrant je třída, nelze aktualizovatelný zámek jen pro čtení na čtení/zápis zámek nebo starší verzi zámku čtení/zápis na zámek jen pro čtení. Provádí se některá z těchto operací vytváří neurčené chování.

### <a name="methods-and-features"></a>Metody a funkce

V následující tabulce jsou uvedeny důležité metody, které jsou definovány `reader_writer_lock` třídy.

|Metoda|Popis|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Získá přístup pro čtení a zápis k zámku.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Pokusí se získat přístup pro čtení a zápis k zámku, ale neblokuje.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Získá přístup jen pro čtení k zámku.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Pokusí se získat přístup jen pro čtení k zámku, ale neblokuje.|
|[Odemknutí](reference/reader-writer-lock-class.md#unlock)|Uvolní zámek.|

[[Horní](#top)]

##  <a name="scoped_lock"></a> scoped_lock a scoped_lock_read –

`critical_section` a `reader_writer_lock` třídy poskytují vnořené pomocné třídy, které zjednodušují způsob práce s objekty vzájemné vyloučení. Tyto pomocné rutiny třídy jsou označovány jako *obor zámků*.

`critical_section` Třída obsahuje [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) třídy. Konstruktoru získá přístup k zadané `critical_section` objekt; přístup verze destruktor na tento objekt. `reader_writer_lock` Třída obsahuje [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) třídu, která se podobá `critical_section::scoped_lock`, s tím rozdílem, že spravuje oprávnění k zápisu do poskytnuté `reader_writer_lock` objektu. `reader_writer_lock` Třída také obsahuje [concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) třídy. Tato třída spravuje přístup pro čtení k zadané `reader_writer_lock` objektu.

S vymezeným oborem zámky poskytuje několik výhod při práci s `critical_section` a `reader_writer_lock` objekty ručně. Obvykle přidělit s vymezeným oborem zámek na zásobníku. S vymezeným oborem zámek uvolní přístup k jeho vzájemné vyloučení objektu automaticky při zničení; proto není odemknutí ručně základní objekt. To je užitečné, když funkce obsahuje více `return` příkazy. S vymezeným oborem zámky může také pomoci psát kód bezpečnost výjimek. Když `throw` příkaz způsobí, že k provedení operace unwind zásobníku, je volán destruktor pro žádný aktivní s vymezeným oborem zámek a proto je vždy správně uvolněny vzájemné vyloučení objektu.

> [!NOTE]
>  Při použití `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, a `reader_writer_lock::scoped_lock_read` třídy, ručně vydané přístup k základní objekt vzájemné vyloučení. Modul runtime tím můžete umístit v neplatném stavu.

##  <a name="event"></a> Události

[Concurrency::event](../../parallel/concrt/reference/event-class.md) třída reprezentuje synchronizační objekt, jehož stav může být signalizován nebo nesignálového. Na rozdíl od synchronizaci objektů, jako je například kritické oddíly, jehož účelem je chránit přístup ke sdíleným datům, synchronizaci události tok spouštění.

`event` Třídy je užitečné, když jeden úkol dokončil práci pro jiné úlohy. Například jeden úkol může signalizovat jiný úkol, že ho má ke čtení dat z připojení k síti nebo ze souboru.

### <a name="methods-and-features"></a>Metody a funkce

Následující tabulka uvádí některé důležité metody, které jsou definovány `event` třídy.

|Metoda|Popis|
|------------|-----------------|
|[Počkej](reference/event-class.md#wait)|Čeká na signálování události.|
|[set](reference/event-class.md#set)|Nastaví událost do signalizovaného stavu.|
|[Resetovat](reference/event-class.md#reset)|Nastaví událost do nesignálového stavu.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Čeká na signálování více událostí.|

### <a name="example"></a>Příklad

Příklad, který ukazuje způsob použití `event` najdete v tématu [porovnávání synchronizačních datových struktur s rozhraním API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Horní](#top)]

## <a name="related-sections"></a>Související oddíly

[Porovnávání synchronizačních datových struktur s rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Porovná chování synchronizačních datových struktur s poskytovaným rozhraním Windows API.

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
Popisuje modulu Runtime souběžnosti, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.

