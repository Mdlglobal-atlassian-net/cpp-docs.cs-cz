---
title: 'Multithreading: Jak používat synchronizační třídy knihovny MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
ms.openlocfilehash: 6115d942abc61fbfc9d60ca1ccf97d4b423ff7c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304649"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>Multithreading: Jak používat synchronizační třídy knihovny MFC

Synchronizace přístup k prostředkům mezi vlákny je běžný problém při psaní aplikací s více vlákny. Má dvě nebo více vláken současně přístupu, kterou stejných dat může vést k nežádoucím a nepředvídatelným výsledkům. Například jedno vlákno může aktualizovat obsah struktury zatímco jiné vlákno čte obsah stejnou strukturu. Není známo, jaká data vlákno pro čtení obdrží: stará data, nově zapsaná data či kombinaci obou. Knihovna MFC poskytuje řadu synchronizace a synchronizační přístupové třídy, které vám pomůže při řešení tohoto problému. Toto téma popisuje třídy, které jsou k dispozici a jak se dají použít k vytvoření třídy bezpečné pro vlákna v typické aplikaci s více vlákny.

Typická aplikace s více vlákny obsahuje třídu, která představuje zdroj soupisu materiálu sdílet mezi vlákny. Plně bezpečným pro vlákno, správně navržená třída nevyžaduje volat jakékoli funkce synchronizace. Všechno, co je do třídy, což vám umožní soustředit se na tom, jak co nejlíp využít třídy, ne o tom, jak může poškodit interně zpracována. Efektivní technikou pro vytvoření třídy plně bezpečným pro vlákno je sloučit třídy synchronizace do třídy prostředků. Slučování synchronizační třídy do sdílené třídy je jednoduchý proces.

Jako příklad trvat, než aplikace, která udržuje odkazovaného seznamu účtů. Tato aplikace umožňuje až tři účty mají být prověřeny v samostatném systému windows, ale pouze jeden je aktualizovat v určitém čase. Při aktualizaci účtu aktualizovaná data se odesílají přes síť do archivní data.

Tato ukázková aplikace používá všechny tři typy synchronizační třídy. Protože to umožňuje až tři účtů najednou, používá [CSemaphore](../mfc/reference/csemaphore-class.md) omezit přístup k tři objekty zobrazení. Při pokusu o zobrazení čtvrtý účtu dojde, aplikace buď čeká, dokud jeden z prvních tří windows zavře nebo se postup nezdaří. Při aktualizaci účtu aplikace používá [CCriticalSection](../mfc/reference/ccriticalsection-class.md) zajistit, že se současně aktualizuje jenom jeden účet. Po úspěšné aktualizaci signály [CEvent](../mfc/reference/cevent-class.md), což uvolní vlákno čeká na událost, která má být signalizován. Toto vlákno odešle nová data do dat archivu.

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Navrhování třídy bezpečné pro vlákna

Chcete-li třída plně bezpečným pro vlákno, nejprve přidáte třídu příslušné synchronizace na sdílené třídy jako datový člen. V předchozím příkladu Správa účtů `CSemaphore` datový člen bude přidán do třídy zobrazení `CCriticalSection` datový člen bude přidán do třídy propojené seznamy a `CEvent` datový člen byly přidány do datové třídy úložiště.

V dalším kroku přidejte volání synchronizaci na všechny členské funkce, které upravují data ve třídě nebo v řízeném prostředku. V každé funkci, měli byste vytvořit buď [CSingleLock](../mfc/reference/csinglelock-class.md) nebo [CMultiLock](../mfc/reference/cmultilock-class.md) a následně zavolat tento objekt `Lock` funkce. Když se zamknout objekt dostane mimo rozsah a je zničen, volá destruktor objektu `Unlock` , uvolnění prostředku. Samozřejmě můžete volat `Unlock` přímo potřebujete.

Navrhování vaší třídy bezpečné pro vlákna tímto způsobem umožňuje použít ve vícevláknových aplikacích jako snadno jako třída vláknově bezpečné, ale s vyšší úrovní zabezpečení. Zapouzdření synchronizační objekt a synchronizaci přístupu k objektu do třídy prostředku poskytuje všechny výhody plně bezpečným pro vlákno programování bez vrácení udržování synchronizace kódu.

Následující příklad kódu ukazuje této metody pomocí datový člen `m_CritSection` (typu `CCriticalSection`), které jsou deklarovány ve třídě sdílený prostředek a `CSingleLock` objektu. Synchronizace sdílený prostředek (odvozený od `CWinThread`) je pokus o vytvoření `CSingleLock` pomocí adresy `m_CritSection` objektu. Je proveden pokus o uzamčení prostředku a po získání práce provádí na sdíleném objektu. Po dokončení práce na prostředek je odemknuté voláním `Unlock`.

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`, na rozdíl od jiné třídy knihovny MFC synchronizace nemá možnost žádosti vypršel časový limit zámku. Čekací doba pro vlákno uvolnění je neomezená.

Nevýhody tohoto přístupu je, že třídy se o něco pomalejší než stejné třídy bez přidání objektů synchronizace. Také pokud je pravděpodobné, že více než jedno vlákno může odstranit objekt, sloučené přístup nemusí vždy fungovat. V takovém případě je lepší zachovat objekty samostatní synchronizace.

Informace o určení, jakou synchronizační třídu použít v různých situacích, naleznete v tématu [Multithreading: Kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md). Další informace o synchronizaci najdete v tématu [synchronizace](/windows/desktop/Sync/synchronization) v sadě Windows SDK. Další informace o podpoře multithreadingu v knihovně MFC, naleznete v tématu [Multithreading s C++ a knihovnou MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
