---
title: "Synchronizační datové struktury | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dd1c47cad01e0324f8027593eb4933f70cd6191
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="synchronization-data-structures"></a>Synchronizační datové struktury
Concurrency Runtime poskytuje několik datové struktury, které umožňují synchronizovat přístup ke sdíleným datům z více vláken. Tyto datové struktury jsou užitečné, když jste sdíleli data, která upravíte zřídka. Objekt synchronizace, například důležitý oddíl, způsobí, že jiná vlákna počkat, dokud sdílený prostředek je k dispozici. Proto pokud používáte takového objektu synchronizovat přístup k datům, která se často používají, byste ztratili škálovatelnost ve vaší aplikaci. [Paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) poskytuje [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) třídy, která umožňuje sdílení prostředků mezi několik vláken nebo úloh bez nutnosti synchronizace. Další informace o `combinable` třídy najdete v tématu [paralelní kontejnery a objekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="top"></a>Oddíly  
 Toto téma popisuje následující typy bloku zpráv asynchronní podrobně:  
  
-   [critical_section](#critical_section)  
  
-   [reader_writer_lock](#reader_writer_lock)  
  
-   [scoped_lock – a scoped_lock_read –](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a>critical_section  
 [Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) třída reprezentuje objekt spolupráci vzájemné vyloučení, která vede k jiným úlohám místo preempting je. Kritické oddíly jsou užitečné, pokud několik vláken vyžadují exkluzivní oprávnění ke čtení a zápis ke sdíleným datům.  

 `critical_section` Třída je nejsou vícenásobně přístupné. [Concurrency::critical_section::lock](reference/critical-section-class.md#lock) metoda výjimku typu [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) Pokud je volána metodou vlákno, které již vlastní zámek.  


  
### <a name="methods-and-features"></a>Metody a funkce  
 V následující tabulce jsou uvedeny důležité metody, které jsou definovány `critical_section` třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[lock](reference/critical-section-class.md#lock)|Získá kritická sekce. Na volání kontextu bloky dokud ho získá zámek.|  
|[try_lock –](reference/critical-section-class.md#try_lock)|Pokusí se získat důležité části, ale nejsou blokovány.|  
|[odemknutí](reference/critical-section-class.md#unlock)|Uvolní kritická sekce.|  
  
 [[Horní](#top)]  
  
##  <a name="reader_writer_lock"></a>reader_writer_lock  
 [Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) třída poskytuje operace vláken pro čtení a zápis ke sdíleným datům. Zámky čtečky nebo zapisovač použijte, pokud několik vláken vyžadují souběžný přístup pro čtení k sdílený prostředek, ale občas zapisovat pro daný sdílený prostředek. Tato třída poskytuje oprávnění k zápisu pouze jedno vlákno na objekt kdykoli.  
  
 `reader_writer_lock` Třídy můžete provádět lepší, než `critical_section` třídy, protože `critical_section` objekt získá výhradní přístup ke sdíleným prostředkům, což zabraňuje souběžný přístup pro čtení.  
  
 Podobně jako `critical_section` třídy, `reader_writer_lock` třída reprezentuje objekt spolupráci vzájemné vyloučení, která vede k jiným úlohám místo preempting je.  
  
 Když vlákno, které musí zapsat do sdíleného prostředku získá zámek pro čtečky/zápis, jiná vlákna, které musí také přístup k prostředku jsou blokován, dokud zapisovač uvolní zámek. `reader_writer_lock` Třída je příkladem *zápisu předvoleb* zámku, která je zámku, která odblokuje zapisovače čekání před jeho odblokuje čtečky čekání.  
  
 Podobně jako `critical_section` třídy, `reader_writer_lock` třída je nejsou vícenásobně přístupné. [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) a [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) metody výjimku typu `improper_lock` Pokud se označují jako vlákno, která již vlastní zámek.  


  
> [!NOTE]
>  Protože `reader_writer_lock` třída je nejsou vícenásobně přístupné, nemůžete upgradovat jen pro čtení zámku na zámek pro čtečky/zápis nebo omezit čtečky nebo zapisovač uzamčení k uzamčení jen pro čtení. Některá z těchto operací provádění vytvoří neurčené chování.  
  
### <a name="methods-and-features"></a>Metody a funkce  
 V následující tabulce jsou uvedeny důležité metody, které jsou definovány `reader_writer_lock` třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[lock](reference/reader-writer-lock-class.md#lock)|Získá přístup pro čtení a zápis pro zámek.|  
|[try_lock –](reference/reader-writer-lock-class.md#try_lock)|Pokusí se získat přístup pro čtení a zápis k zámek, ale nejsou blokovány.|  
|[lock_read –](reference/reader-writer-lock-class.md#lock_read)|Získá přístup jen pro čtení k zámek.|  
|[try_lock_read –](reference/reader-writer-lock-class.md#try_lock_read)|Pokusí se získat přístup jen pro čtení k zámek, ale nejsou blokovány.|  
|[odemknutí](reference/reader-writer-lock-class.md#unlock)|Uvolní zámek.|  
  
 [[Horní](#top)]  
  
##  <a name="scoped_lock"></a>scoped_lock – a scoped_lock_read –  
 `critical_section` a `reader_writer_lock` třídy poskytují vnořené pomocných tříd, které zjednodušují způsob práce s objekty vzájemné vyloučení. Tyto pomocné třídy se označují jako *obor zámků*.  
  
 `critical_section` Třída obsahuje [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) třídy. V konstruktoru získá přístup k zadanému `critical_section` objekt; destruktor verzích přístup k objektu. `reader_writer_lock` Třída obsahuje [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) třídy, která se podobá `critical_section::scoped_lock`kromě toho, že spravuje přístup k zápisu do zadaných `reader_writer_lock` objektu. `reader_writer_lock` Třída také obsahuje [concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) třídy. Tato třída spravuje přístup pro čtení k poskytnutého `reader_writer_lock` objektu.  

  
 Vymezená zámky poskytují několik výhod, když pracujete s `critical_section` a `reader_writer_lock` objekty ručně. Obvykle přidělit vymezená zámku v zásobníku. Vymezená zámku uvolní přístup k jeho vzájemné vyloučení objekt automaticky při byla; proto není odemknutí ručně podkladových objektů. To je užitečné, když funkce obsahuje více `return` příkazy. Vymezená zámky také můžete napsat kód výjimky bezpečné. Když `throw` příkaz způsobuje zásobníku unwind, se nazývá destruktor pro všechny aktivní vymezená zámku a proto vždy správně uvolnění objektu vzájemné vyloučení.  
  
> [!NOTE]
>  Při použití `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, a `reader_writer_lock::scoped_lock_read` třídy, ručně vydané přístup k základní objekt vzájemné vyloučení. To můžete vložit modulu runtime v neplatném stavu.  
  
##  <a name="event"></a>události  
 [Concurrency::event](../../parallel/concrt/reference/event-class.md) třída reprezentuje na synchronizační objekt, jehož stavu můžete signál nebo jiný signál. Na rozdíl od synchronizace objekty, například kritické oddíly, jejichž účelem je chránit přístup ke sdíleným datům, události synchronizovat toku spouštění.  
  
 `event` Třída je užitečné, když jeden úkol dokončil práci pro jiná úloha. Například jeden úkol může signalizovat jiná úloha že ji má ke čtení dat z připojení k síti nebo ze souboru.  
  
### <a name="methods-and-features"></a>Metody a funkce  
 Následující tabulka uvádí některé důležité metody, které jsou definovány `event` třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Počkej](reference/event-class.md#wait)|Čeká na událost, která má být signál.|  
|[set](reference/event-class.md#set)|Nastaví událost do signalizovaného stavu.|  
|[resetování](reference/event-class.md#reset)|Nastaví událost do stavu signál.|  
|[wait_for_multiple –](reference/event-class.md#wait_for_multiple)|Čeká na více událostí k stát signál.|  

  
### <a name="example"></a>Příklad  
 Pro příklad, který ukazuje způsob použití `event` třídy najdete v tématu [porovnávání synchronizačních datových struktur rozhraní API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Horní](#top)]  
  
## <a name="related-sections"></a>Související oddíly  
 [Porovnávání synchronizačních datových struktur s rozhraním API systému Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 Porovná chování synchronizační datové struktury k protokolům poskytovaným rozhraní API systému Windows.  
  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)  
 Popisuje Concurrency Runtime, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.

