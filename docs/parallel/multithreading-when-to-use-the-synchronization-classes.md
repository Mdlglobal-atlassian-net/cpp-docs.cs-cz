---
title: 'Multithreading: Kdy použít synchronizační třídy knihovny MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
ms.openlocfilehash: cb68487e036093ce4718c39c18c9d1e75afe0f7c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511997"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Multithreading: Kdy použít synchronizační třídy knihovny MFC

Třídy s více vlákny poskytované knihovnou MFC spadají do dvou kategorií: objekty synchronizace ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [CCriticalSection](../mfc/reference/ccriticalsection-class.md)a [CEvent](../mfc/reference/cevent-class.md)) a objekty pro přístup k synchronizaci ([ CMultiLock](../mfc/reference/cmultilock-class.md) a [CSingleLock](../mfc/reference/csinglelock-class.md)).

Synchronizační třídy se používají, když je nutné řídit přístup k prostředku, aby se zajistila integrita prostředku. Třídy přístupu k synchronizaci slouží k získání přístupu k těmto řízeným prostředkům. Toto téma popisuje, kdy použít jednotlivé třídy.

Chcete-li zjistit, kterou synchronizační třídu byste měli použít, položte si následující řadu otázek:

1. Je nutné, aby aplikace čekala na to, že se něco stalo, než bude moci získat přístup k prostředku (například data musí být přijímána z komunikačního portu, než může být zapsána do souboru)?

   Pokud ano, použijte `CEvent`.

2. Může více než jedno vlákno v rámci stejné aplikace přistupovat k tomuto prostředku najednou (například vaše aplikace umožňuje až pět oken s zobrazeními ve stejném dokumentu)?

   Pokud ano, použijte `CSemaphore`.

3. Může tento prostředek používat více než jedna aplikace (například prostředek je v knihovně DLL)?

   Pokud ano, použijte `CMutex`.

   Pokud ne, použijte `CCriticalSection`.

`CSyncObject`se nikdy nepoužívá přímo. Je základní třídou pro ostatní čtyři třídy synchronizace.

## <a name="example-1-using-three-synchronization-classes"></a>Příklad 1: Použití tří synchronizačních tříd

Jako příklad si povezměte aplikaci, která udržuje propojený seznam účtů. Tato aplikace umožňuje prozkoumat až tři účty v samostatných oknech, ale v jakémkoli čase se dá aktualizovat jenom jedna. Po aktualizaci účtu se aktualizovaná data odesílají přes síť do archivu dat.

Tato ukázková aplikace používá všechny tři typy synchronizačních tříd. Vzhledem k tomu, že umožňuje prozkoumat až tři účty najednou, používá `CSemaphore` se k omezení přístupu k třem objektům zobrazení. Když dojde k pokusu o zobrazení čtvrtého účtu, aplikace buď počká, dokud se jedna z prvních tří oken nezavře, nebo dojde k chybě. Když se účet aktualizuje, aplikace používá `CCriticalSection` nástroj, aby se zajistilo, že se v jednu chvíli aktualizuje jenom jeden účet. Po úspěšném dokončení aktualizace signalizuje `CEvent`, že uvolní vlákno, které čeká na signál události. Toto vlákno odesílá nová data do archivu dat.

## <a name="example-2-using-synchronization-access-classes"></a>Příklad 2: Použití synchronizačních tříd přístupu

Volba, kterou synchronizační třídu přístupu použít, je ještě jednodušší. Pokud má vaše aplikace přístup pouze k jednomu kontrolovanému prostředku, použijte `CSingleLock`. Pokud potřebuje přístup k některému z několika kontrolovaných prostředků, použijte `CMultiLock`. V příkladu 1 `CSingleLock` by se použila, protože v každém případě je potřeba jenom jeden prostředek v určitou dobu.

Informace o použití synchronizačních tříd naleznete v tématu [Multithreading: Jak používat synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md). Informace o synchronizaci najdete v tématu [synchronizace](/windows/win32/Sync/synchronization) v Windows SDK. Informace o podpoře multithreadingu v knihovně MFC naleznete v tématu [Multithreading s C++ a MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
