---
title: Synchronizační datové struktury
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 85dec6b003330a3560ae1dcc5c41b5e6d49f765e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142795"
---
# <a name="synchronization-data-structures"></a>Synchronizační datové struktury

Concurrency Runtime poskytuje několik datových struktur, které umožňují synchronizovat přístup ke sdíleným datům z více vláken. Tyto datové struktury jsou užitečné, když máte sdílená data, která upravujete zřídka. Synchronizační objekt, například kritická část, způsobí, že jiná vlákna počká, až bude sdílený prostředek k dispozici. Proto pokud tento objekt použijete k synchronizaci přístupu k datům, která se používají často, můžete ztratit škálovatelnost ve vaší aplikaci. [Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md) poskytuje třídu [Concurrency::](../../parallel/concrt/reference/combinable-class.md) kombinovatelné, která umožňuje sdílení prostředků mezi několika vlákny nebo úkoly bez nutnosti synchronizace. Další informace o třídě `combinable` naleznete v tématu [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="top"></a>Řezů

Toto téma popisuje následující typy asynchronních bloků zpráv podrobněji:

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock a scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a>critical_section

Třída [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) představuje společný objekt pro vyloučení vzájemného vyloučení, který vede k jiným úlohám, a nemusíte ho zastavovat. Důležité části jsou užitečné v případě, že více vláken vyžaduje exkluzivní přístup pro čtení a zápis ke sdíleným datům.

Třída `critical_section` není znovu určena. Metoda [Concurrency:: critical_section:: Lock](reference/critical-section-class.md#lock) vyvolá výjimku typu [concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md) , pokud je volána vláknem, který je již vlastníkem zámku.

### <a name="methods-and-features"></a>Metody a funkce

V následující tabulce jsou uvedeny důležité metody, které jsou definovány třídou `critical_section`.

|Metoda|Popis|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Získá kritickou část. Volající kontext blokuje, dokud nezíská zámek.|
|[try_lock](reference/critical-section-class.md#try_lock)|Pokusí se získat kritickou sekci, ale neblokuje.|
|[Uzamknout](reference/critical-section-class.md#unlock)|Uvolní oddíl kritického.|

[[Nahoře](#top)]

## <a name="reader_writer_lock"></a>reader_writer_lock

Třída [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) poskytuje operace čtení/zápisu bezpečné pro přístup z více vláken ke sdíleným datům. Používejte zámky čtecího modulu nebo zapisovače, pokud více vláken vyžaduje souběžný přístup pro čtení ke sdílenému prostředku, ale jen zřídka zapisuje do tohoto sdíleného prostředku Tato třída poskytuje přístup pouze k jednomu vláknu s přímým přístupem k objektu.

Třída `reader_writer_lock` může pracovat lépe než `critical_section` třídy, protože objekt `critical_section` získává exkluzivní přístup ke sdílenému prostředku, který brání souběžnému přístupu pro čtení.

Podobně jako třída `critical_section`, třída `reader_writer_lock` představuje společný objekt pro vyloučení vzájemného vyloučení, který vede k jiným úlohám namísto jejich přerušení.

Když vlákno, které musí zapisovat do sdíleného prostředku, získá zámek pro čtení/zápis, budou další vlákna, která také musí přistupovat k prostředku, blokovaná, dokud zapisovač neuvolní zámek. Třída `reader_writer_lock` je příkladem zámku *s možností zápisu* , který je zámek, který odblokuje čekání na zapisovače předtím, než odblokuje čekající čtečky.

Podobně jako třída `critical_section`, `reader_writer_lock` třída není znovu přidaná. Metody [Concurrency:: reader_writer_lock:: Lock](reference/reader-writer-lock-class.md#lock) a [concurrency:: reader_writer_lock:: lock_read](reference/reader-writer-lock-class.md#lock_read) vyvolávají výjimku typu `improper_lock`, pokud jsou volány vláknem, které už je vlastníkem zámku.

> [!NOTE]
> Vzhledem k tomu, že třída `reader_writer_lock` není znovu určená, nemůžete upgradovat zámek jen pro čtení na zámek čtenář/Writer nebo snížit zámek čtenář/zapisovače na zámek jen pro čtení. Provádění některé z těchto operací vytvoří nespecifikované chování.

### <a name="methods-and-features"></a>Metody a funkce

V následující tabulce jsou uvedeny důležité metody, které jsou definovány třídou `reader_writer_lock`.

|Metoda|Popis|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Získá přístup pro čtení a zápis pro zámek.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Pokusí se získat přístup pro čtení a zápis k zámku, ale neblokuje.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Získá přístup k zámku jen pro čtení.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Pokusí se získat přístup k zámku, který je jen pro čtení, ale neblokuje.|
|[Uzamknout](reference/reader-writer-lock-class.md#unlock)|Uvolní zámek.|

[[Nahoře](#top)]

## <a name="scoped_lock"></a>scoped_lock a scoped_lock_read

Třídy `critical_section` a `reader_writer_lock` poskytují vnořené pomocné třídy, které zjednodušují způsob práce s objekty vzájemného vyloučení. Tyto pomocné třídy se označují jako *zámky s oborem*.

Třída `critical_section` obsahuje třídu [Concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) . Konstruktor získá přístup k poskytnutému objektu `critical_section`; destruktor uvolní přístup k tomuto objektu. Třída `reader_writer_lock` obsahuje třídu [Concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) , která se podobá `critical_section::scoped_lock`, s tím rozdílem, že spravuje přístup pro zápis k poskytnutému `reader_writer_lock` objektu. Třída `reader_writer_lock` obsahuje také třídu [Concurrency:: reader_writer_lock:: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) . Tato třída spravuje přístup pro čtení k poskytnutému objektu `reader_writer_lock`.

Pokud pracujete s objekty `critical_section` a `reader_writer_lock` ručně, zablokované zámky poskytují několik výhod. Obvykle přidělíte rozsah zámku v zásobníku. Vymezený zámek uvolňuje automaticky přístup k objektu vzájemného vyloučení, když je zničen; Proto neodemknete ručně základní objekt. To je užitečné v případě, že funkce obsahuje více příkazů `return`. Zámky s vymezeným oborem vám také pomůžou napsat kód bezpečný pro výjimku. Když příkaz `throw` způsobí unwind zásobníku, je zavolán destruktor pro libovolný aktivní rozsah zámku, a proto je objekt vzájemného vyloučení vždy správně uvolněn.

> [!NOTE]
> Pokud používáte třídy `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`a `reader_writer_lock::scoped_lock_read`, neprovádějte ruční uvolnění přístupu k základnímu objektu vzájemného vyloučení. To může modul runtime vložit do neplatného stavu.

## <a name="event"></a>událostí

Třída [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) představuje synchronizační objekt, jehož stav může být signalizace nebo bez signalizace. Na rozdíl od synchronizačních objektů, jako jsou důležité oddíly, jejichž účelem je chránit přístup ke sdíleným datům, události synchronizují tok provádění.

Třída `event` je užitečná v případě, že jeden úkol dokončil práci pro jiný úkol. Například jeden úkol může signalizovat jiný úkol, který má číst data ze síťového připojení nebo ze souboru.

### <a name="methods-and-features"></a>Metody a funkce

Následující tabulka ukazuje několik důležitých metod, které jsou definovány třídou `event`.

|Metoda|Popis|
|------------|-----------------|
|[Počkej](reference/event-class.md#wait)|Čeká, až se událost přestane signalizovat.|
|[set](reference/event-class.md#set)|Nastaví událost na stav signalizace.|
|[nové](reference/event-class.md#reset)|Nastaví událost na stav bez signálu.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Čeká, až se zasignalizují více událostí.|

### <a name="example"></a>Příklad

Příklad, který ukazuje použití třídy `event`, naleznete v tématu [porovnání datových struktur synchronizace s rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Nahoře](#top)]

## <a name="related-sections"></a>Související oddíly

[Porovnávání synchronizačních datových struktur s rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Porovnává chování datových struktur synchronizace s daty poskytovanými rozhraním API systému Windows.

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
Popisuje Concurrency Runtime, který zjednodušuje paralelní programování a obsahuje odkazy na Příbuzná témata.
