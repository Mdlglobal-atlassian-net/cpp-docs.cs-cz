---
title: 'Multithreading: jak používat synchronizační třídy knihovny MFC'
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
ms.openlocfilehash: ef76199813de417d2aa57eb7f3f15ae4d2fefc56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140493"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>Multithreading: jak používat synchronizační třídy knihovny MFC

Synchronizace přístupu k prostředkům mezi vlákny je běžný problém při psaní vícevláknových aplikací. Pokud mají dvě nebo více vláken současně přístup ke stejným datům, může to vést k nežádoucím a nepředvídatelným výsledkům. Například jedno vlákno může aktualizovat obsah struktury, zatímco jiné vlákno čte obsah stejné struktury. Není známo, jaká data vlákno pro čtení obdrží: stará data, nově zapsaná data či kombinaci obou. Knihovna MFC poskytuje řadu synchronizačních a synchronizačních tříd přístupu, které pomáhají při řešení tohoto problému. Toto téma vysvětluje třídy, které jsou k dispozici, a jejich použití k vytváření tříd bezpečných pro přístup z více vláken v typických aplikacích s více vlákny.

Typická vícevláknová aplikace má třídu, která představuje prostředek pro sdílení mezi vlákny. Správně navržená plně třída bezpečná pro přístup z více vláken nevyžaduje volání jakékoli synchronizační funkce. Vše je zpracováváno interně pro třídu, což vám umožní soustředit se na to, jak nejlépe využít třídu, nikoli o tom, jak se může poškodit. Efektivní technikou pro vytváření zcela bezpečné třídy pro přístup z více vláken je sloučit synchronizační třídu s třídou prostředků. Sloučení tříd synchronizace do sdílené třídy je jednoduchý proces.

Jako příklad si povezměte aplikaci, která udržuje propojený seznam účtů. Tato aplikace umožňuje prozkoumat až tři účty v samostatných oknech, ale v jakémkoli čase se dá aktualizovat jenom jedna. Po aktualizaci účtu se aktualizovaná data odesílají přes síť do archivu dat.

Tato ukázková aplikace používá všechny tři typy synchronizačních tříd. Vzhledem k tomu, že umožňuje prozkoumat až tři účty v jednom okamžiku, používá [CSemaphore](../mfc/reference/csemaphore-class.md) k omezení přístupu k třem objektům zobrazení. Když dojde k pokusu o zobrazení čtvrtého účtu, aplikace buď počká, dokud se jedna z prvních tří oken nezavře, nebo dojde k chybě. Když se účet aktualizuje, aplikace používá [CCriticalSection](../mfc/reference/ccriticalsection-class.md) , aby se zajistilo, že se v jednom okamžiku aktualizuje jenom jeden účet. Po úspěšném dokončení aktualizace signalizuje [CEvent](../mfc/reference/cevent-class.md), který uvolní vlákno čekající na signál události. Toto vlákno odesílá nová data do archivu dat.

## <a name="_mfc_designing_a_thread.2d.safe_class"></a>Návrh třídy bezpečné pro přístup z více vláken

Aby třída byla plně bezpečná pro přístup z více vláken, nejprve do sdílených tříd přidejte příslušnou synchronizační třídu jako datový člen. V předchozím příkladu správy účtu by se do třídy zobrazení přidal datový člen `CSemaphore`, datový člen `CCriticalSection` by se přidal do třídy s propojenými seznamy a do třídy úložiště dat by se přidal datový člen `CEvent`.

Dále přidejte synchronizační volání do všech členských funkcí, které upraví data ve třídě nebo přistupují k kontrolovanému prostředku. V každé funkci byste měli vytvořit objekt [CSingleLock](../mfc/reference/csinglelock-class.md) nebo [CMultiLock](../mfc/reference/cmultilock-class.md) a volat funkci `Lock` objektu. Když je objekt zámku mimo rozsah a je zničen, volá destruktor objektu `Unlock` za vás a uvolní prostředek. Samozřejmě můžete volat `Unlock` přímo, pokud chcete.

Návrh třídy bezpečné pro přístup z více vláken v tomto způsobu umožňuje jejich použití ve vícevláknové aplikaci stejně snadno jako třídu, která není bezpečná pro přístup z více vláken, ale s vyšší úrovní zabezpečení. Zapouzdření synchronizačního objektu a objektu pro přístup k synchronizaci do třídy prostředku poskytuje všechny výhody plně bezpečného programování pro vlákna bez nutnosti zachovat kód synchronizace.

Následující příklad kódu ukazuje tuto metodu pomocí datového členu `m_CritSection` (typu `CCriticalSection`) deklarovaného ve třídě sdíleného prostředku a objektu `CSingleLock`. Synchronizace sdíleného prostředku (odvozená z `CWinThread`) se pokouší vytvořit objekt `CSingleLock` pomocí adresy objektu `m_CritSection`. Došlo k pokusu o uzamčení prostředku a při jeho získání bude práce provedena na sdíleném objektu. Po dokončení práce je prostředek odemčený voláním `Unlock`.

```cpp
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`, na rozdíl od jiných synchronizačních tříd knihovny MFC, nemá možnost časově omezená žádost o zámek. Čekací doba, po kterou se vlákno stane volno, je nekonečná.

Nevýhodami tohoto přístupu je, že třída bude mírně pomalejší než stejná třída bez přidaných synchronizačních objektů. Také pokud existuje možnost, že více než jeden podproces může odstranit objekt, sloučený přístup nemusí vždy fungovat. V této situaci je lepší udržovat samostatné synchronizační objekty.

Informace o určení, kterou synchronizační třídu použít v různých situacích, naleznete v tématu [Multithreading: Kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md). Další informace o synchronizaci najdete v tématu [synchronizace](/windows/win32/Sync/synchronization) v Windows SDK. Další informace o podpoře multithreadingu v knihovně MFC naleznete v tématu [Multithreading s C++ a MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
