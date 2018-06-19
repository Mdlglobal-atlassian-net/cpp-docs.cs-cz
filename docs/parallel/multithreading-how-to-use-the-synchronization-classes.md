---
title: 'Multithreading: Jak používat synchronizační třídy | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49b0737a794216c4899b280bc049a1cdc0fe0948
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689022"
---
# <a name="multithreading-how-to-use-the-synchronization-classes"></a>Multithreading: Jak používat synchronizační třídy
Synchronizace přístupu k prostředkům mezi vlákny problém je běžný, při zápisu vícevláknové aplikace. Má dva nebo více vlákna současně přístup, stejná data může vést k nežádoucím a nepředvídatelným výsledky. Například jedno vlákno může aktualizovat obsah struktury zatímco jiné vlákno čte obsah stejnou strukturu. Není známo, jaká data vlákno pro čtení obdrží: stará data, nově zapsaná data či kombinaci obou. MFC poskytuje řadu synchronizace a synchronizační přístupové třídy na pomoc při řešení tohoto problému. Toto téma vysvětluje třídy, které jsou k dispozici a jakým způsobem je použít k vytvoření třídy bezpečné pro přístup z více vláken v typické aplikaci s více vlákny.  
  
 Typická vícevláknové aplikace obsahuje třídu, která představuje zdroj k sdílení mezi vlákny. Třídu správně navrženou, plně bezpečné pro přístup z více vláken nevyžaduje volat jakékoli funkce synchronizace. Všechno, co se zpracovává interně k třídě, což vám umožní soustředit na tom, jak nejlépe využít třídy, ne tom, jak může získat poškozený. Efektivní technika pro vytvoření třídy plně bezpečné pro přístup z více vláken je sloučit synchronizační třídu do třídy prostředků. Slučování synchronizační třídy do sdílené třídy je jednoduchý proces.  
  
 Jako příklad trvat aplikaci, která udržuje seznam propojené účty. Tato aplikace umožňuje až tři účtů v samostatném systému windows, ale lze aktualizovat pouze jeden konkrétní kdykoli. Při aktualizaci účtu je aktualizovaná data odešlou přes síť dat archivu.  
  
 Tato ukázková aplikace používá všechny tři typy třídy synchronizace. Protože umožňuje v jednom okamžiku až tři účty, používá [prohlížení](../mfc/reference/csemaphore-class.md) omezit přístup k tři objekty zobrazení. Při pokusu o zobrazení účet čtvrtý dojde, aplikace buď čeká, dokud jeden z prvních tří windows zavře nebo se nezdaří. Při aktualizaci účtu používá aplikace [CCriticalSection](../mfc/reference/ccriticalsection-class.md) zajistit, že je najednou aktualizován pouze jeden účet. Po úspěšné aktualizaci signalizuje [CEvent](../mfc/reference/cevent-class.md), což uvolní vlákno čeká na signál události. Tento přístup z více vláken odešle nová data do dat archivu.  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Navrhování třídy bezpečné pro přístup z více vláken  
 Chcete-li třídu plně bezpečné pro přístup z více vláken, nejprve přidejte třídu příslušné synchronizace do sdílené třídy jako člena. V předchozím příkladu Správa účtů **prohlížení** – datový člen by byl přidán do zobrazení třídy `CCriticalSection` – datový člen by byl přidán k třídě-list a `CEvent` – datový člen by byl přidán k datům třídy úložiště.  
  
 Dále přidejte volání všechny členské funkce, které upravují data ve třídě nebo získat přístup k prostředku řízené synchronizace. V každé funkci, měli byste vytvořit buď [CSingleLock](../mfc/reference/csinglelock-class.md) nebo [CMultiLock](../mfc/reference/cmultilock-class.md) objektu a tento objekt volání `Lock` funkce. Pokud je objekt zámku ocitne mimo obor a zničen, volání destruktoru objektu `Unlock` , vydání prostředku. Samozřejmě můžete volat `Unlock` přímo podle potřeby.  
  
 Navrhování vaší třídy bezpečné pro přístup z více vláken tímto způsobem umožňuje použít v vícevláknové aplikace jako snadno jako třída není bezpečná pro přístup z více vláken, ale s vyšší úrovní zabezpečení. Zapouzdření synchronizace objektu a synchronizace přístupu objektu do třídy prostředku poskytuje všechny výhody programování plně bezpečné pro přístup z více vláken bez navracení zachování synchronizace kódu.  
  
 Následující příklad kódu ukazuje tuto metodu, pomocí datový člen `m_CritSection` (typu `CCriticalSection`), deklarované v třídě sdílený prostředek a `CSingleLock` objektu. Synchronizace sdílený prostředek (odvozený z `CWinThread`) je pokus o vytvoření `CSingleLock` objektu pomocí adresy `m_CritSection` objektu. K pokusu o uzamčení prostředku a, když získají, práci na sdíleném objektu. Po dokončení práce se daný prostředek k odemknout pomocí volání `Unlock`.  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  `CCriticalSection`, na rozdíl od jiných synchronizační třídy MFC nemá možnost časově uzamknout žádost. Čekací dobu uvolnění vlákna je nekonečno.  
  
 Nevýhody tohoto přístupu je, že třídy se nepatrně pomalejší než třída bez přidání objektů synchronizace. Navíc pokud je pravděpodobné, že více než jedno vlákno může odstranit objekt, sloučený přístup nemusí vždy fungovat. V takovém případě je lepší udržovat samostatné objekty synchronizace.  
  
 Informace o způsobu určení, které třídy pro použití v různých situacích naleznete v tématu [Multithreading: kdy použít synchronizační třídy](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Další informace o synchronizaci najdete v tématu [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Další informace o podpoře více vláken v prostředí MFC najdete v tématu [Multithreading s C++ a MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)