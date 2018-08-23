---
title: 'Multithreading: Kdy použít synchronizační třídy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3556bace6c578edec8eaedffb528d21cb1644f5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606061"
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>Multithreading: Kdy použít synchronizační třídy
Třídy s více vlákny s knihovnou MFC k dispozici spadají do dvou kategorií: Synchronizace objektů ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), a [CEvent](../mfc/reference/cevent-class.md)) a přístup k objektům synchronizace ([CMultiLock](../mfc/reference/cmultilock-class.md) a [CSingleLock](../mfc/reference/csinglelock-class.md)).  
  
Třídy synchronizace se používají při přístupu k prostředku musí řídit k zajištění integrity prostředku. Synchronizační přístupové třídy se používají k získání přístupu k těmto prostředkům řízené. Toto téma popisuje, kdy používat jednotlivé třídy.  
  
Pokud chcete zjistit, jakou synchronizační třídu byste měli použít, požádejte následující několik otázek:  
  
1. Čekání na něco, co můžete provést před vytvořením měl přístup k prostředku nemá aplikace (například data musí být přijata z komunikačních portů předtím, než může být zapsán do souboru)?  
  
     Pokud ano, použít `CEvent`.  
  
2. Můžete více než jedno vlákno v rámci stejné aplikaci přístup k tomuto prostředku najednou (například vaše aplikace umožňuje až pět oken s názory na stejném dokumentu)?  
  
     Pokud ano, použít `CSemaphore`.  
  
3. Můžete použít více než jednu aplikaci tohoto prostředku (například prostředek je v knihovně DLL)?  
  
     Pokud ano, použít `CMutex`.  
  
     Pokud ne, použijte `CCriticalSection`.  
  
`CSyncObject` nikdy slouží přímo. Je základní třída pro jiné třídy čtyři synchronizace.  
  
## <a name="example-1-using-three-synchronization-classes"></a>Příklad 1: Použití tří synchronizační třídy  
 
Jako příklad trvat, než aplikace, která udržuje odkazovaného seznamu účtů. Tato aplikace umožňuje až tři účty mají být prověřeny v samostatném systému windows, ale pouze jeden je aktualizovat v určitém čase. Při aktualizaci účtu aktualizovaná data se odesílají přes síť do archivní data.  
  
Tato ukázková aplikace používá všechny tři typy synchronizační třídy. Protože to umožňuje až tři účtů najednou, používá `CSemaphore` omezit přístup k tři objekty zobrazení. Při pokusu o zobrazení čtvrtý účtu dojde, aplikace buď čeká, dokud jeden z prvních tří windows zavře nebo se postup nezdaří. Při aktualizaci účtu aplikace používá `CCriticalSection` zajistit, že se současně aktualizuje jenom jeden účet. Po úspěšné aktualizaci signály `CEvent`, což uvolní vlákno čeká na událost, která má být signalizován. Toto vlákno odešle nová data do dat archivu.  
  
## <a name="example-2-using-synchronization-access-classes"></a>Příklad 2: Použití tříd pro přístup k synchronizaci  
 
Zvolíte, jakou synchronizační třídu přístup k použití je ještě jednodušší. Pokud se týká pouze na jeden prostředek řízený přístup k vaší aplikace, použijte `CSingleLock`. Pokud nepotřebuje přístup k libovolnému počtu kontrolovaných prostředků, použijte `CMultiLock`. V příkladu 1 `CSingleLock` by byla použita, protože v každém případě je potřeba jenom jeden prostředek v určitém čase.  
  
Informace o tom, jak použít synchronizační třídy naleznete v tématu [Multithreading: jak používat synchronizační třídy](../parallel/multithreading-how-to-use-the-synchronization-classes.md). Informace o synchronizaci najdete v tématu [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v sadě Windows SDK. Informace o podpoře multithreadingu v knihovně MFC, naleznete v tématu [Multithreading s C++ a knihovnou MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 
[Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)