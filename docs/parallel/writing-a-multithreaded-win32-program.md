---
title: "Psaní programů s více vlákny Win32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ede0e6dc1740f93f4905dc69b1927aee0d1a7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="writing-a-multithreaded-win32-program"></a>Psaní programů s více vlákny pro prostředí Win32
Při psaní programů s více vlákny musí koordinovat jejich chování a [využití prostředků programu](#_core_sharing_common_resources_between_threads). Také musíte zkontrolovat, že každé vlákno obdrží [vlastní zásobník](#_core_thread_stacks).  
  
##  <a name="_core_sharing_common_resources_between_threads"></a>Sdílení společných prostředků mezi vlákny  
  
> [!NOTE]
>  Podobné informace z hlediska MFC, najdete v části [Multithreading: tipy pro programování](../parallel/multithreading-programming-tips.md) a [Multithreading: kdy použít synchronizační třídy](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  
  
 Každé vlákno má svůj vlastní zásobník a zaregistruje vlastní kopii procesoru. Další prostředky, jako jsou soubory, statických dat a paměť haldy, jsou sdíleny všechna vlákna v procesu. Vlákna používají tyto společné prostředky musí být synchronizovány. Win32 poskytuje několik způsobů, jak synchronizovat prostředků, včetně semaforů, kritické oddíly, události a mutex – třídy.  
  
 Pokud přístup k více vláken statických dat, musí zadat váš program možné zdroje konfliktů. Zvažte program, kde jedno vlákno aktualizuje struktura statických dat obsahující *x*,*y* souřadnice pro položky, které mají být zobrazeny v jiné vlákno. Pokud aktualizace vlákno mění *x* koordinaci a je zrušené, abyste mohli změnit *y* souřadnic, může být zobrazení vlákno naplánován před *y* souřadnice je Aktualizovat. Položka bude zobrazena na nesprávné umístění. Tento problém můžete vyhnout použitím semaforů k řízení přístupu na strukturu.  
  
 Mutex (zkratka pro *vzájemně*protokolování přístupu uživatele *ex*clusion) je způsob komunikace mezi vlákny nebo procesy, které jsou vzájemně asynchronně. Tato komunikace se obvykle používá ke koordinaci aktivit s více vlákny nebo procesy, obvykle pomocí řízení přístupu ke sdíleným prostředkům zamykání a odemykání prostředku. Chcete-li tento problém vyřešit *x*,*y* problém s aktualizací souřadnice, vlákno aktualizace nastaví mutex označující, že je datová struktura používána před provedením aktualizace. To by mělo odstranit mutex po zpracoval oba souřadnice. Zobrazení vláken musí počkat mutex být zrušte před aktualizací zobrazení. Tento proces čekání na mutex se často nazývá blokování na mutex, protože tento proces je blokovaný a nemůže pokračovat, dokud se nevymaže mutex.  
  
 Program Bounce.c ukazuje [Ukázkový vícevláknový C Program](../parallel/sample-multithread-c-program.md) používá mutex s názvem `ScreenMutex` pro koordinaci aktualizací obrazovky. Pokaždé, když jeden zobrazení vláken je připraven k zápisu na obrazovku, zavolá **WaitForSingleObject** spolu s `ScreenMutex` a konstantní **NEKONEČNÉ** k označení, že  **WaitForSingleObject** volání by měly blokovat na mutex a není vypršení časového limitu. Pokud `ScreenMutex` je zřejmé, čekací funkce nastaví mutex, takže jiné vlákna nesmí zasahovat zobrazení a pokračuje v provádění vlákna. Vlákno, jinak hodnota zablokuje, dokud mutex vymazán. Po dokončení aktualizace zobrazení vlákno uvolní mutex voláním **ReleaseMutex**.  
  
 Zobrazí obrazovky a statických dat jsou pouze dvě vyžadující pečlivé řízení zdrojů. Například váš program může mít přístup ke stejnému souboru více vláken. Protože jiné vlákno může přesunout ukazatele souboru, musí každé vlákno před čtení nebo zápis obnovit ukazatele souboru. Každé vlákno kromě toho musí Ujistěte se, že není zrušené mezi ukazatele čas a čas, který přistupuje k souboru. Tyto vlákna by měla použít semafor pro koordinaci přístupu k souboru pomocí "bracketing" každého přístupu k souboru s **WaitForSingleObject** a **ReleaseMutex** volání. Tento postup ukazuje následující příklad kódu:  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a>Zásobníky vlákna  
 Všechny výchozí prostor v zásobníku aplikace je přidělená k první podproces provádění, což se označuje jako vlákno 1. V důsledku toho je nutné zadat, kolik paměti k přidělení pro jednotlivé zásobníky pro každé další vlákno váš program vyžaduje. Operační systém v případě potřeby přiděluje další prostor v zásobníku pro vlákno, ale musíte zadat výchozí hodnotu.  
  
 První argument ve `_beginthread` volání je ukazatel **BounceProc** funkce, která zpracuje vlákna. Druhý argument určuje výchozí velikost zásobníku pro vlákno. Poslední argument je číslo ID, který je předán do **BounceProc**. **BounceProc** používá číslo ID pro generátoru náhodných čísel, aby vyberte atribut vlákna barva a zobrazení znaku.  
  
 Vláken, která volají běhové knihovny jazyka C a Win32 API musí poskytovat dostatečné místo zásobníku pro knihovnu a funkce rozhraní API, které volají. C `printf` funkce vyžaduje více než 500 bajtů místa v zásobníku a při volání rozhraní API Win32 rutiny byste měli mít k 2 kB volného místa zásobníku.  
  
 Protože každý podproces má vlastní zásobník, se můžete vyhnout potenciální kolizí položkami dat pomocí tak málo statických dat co nejmenší. Návrh vašeho programu používat automatické proměnné zásobníku pro všechna data, která může být privátní na vlákno. Pouze globální proměnné v aplikaci Bounce.c jsou objekty mutex nebo proměnné, které nikdy změnit po jejich inicializaci.  
  
 Win32 také poskytuje úložiště Thread Local (TLS) k uložení dat pro vlákno. Další informace najdete v tématu [vláken místní úložiště (TLS)](../parallel/thread-local-storage-tls.md).  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)