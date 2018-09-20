---
title: Psaní programů s více vlákny pro Win32 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf9be32b4e9f9d46be9c3aa6f2b80a331a18ea67
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386265"
---
# <a name="writing-a-multithreaded-win32-program"></a>Psaní programů s více vlákny pro prostředí Win32

Při psaní programů s více vlákny je třeba koordinovat jejich chování a [využívání prostředků programu](#_core_sharing_common_resources_between_threads). Také musíte zkontrolovat, že každé vlákno obdrží [vlastní zásobník](#_core_thread_stacks).

##  <a name="_core_sharing_common_resources_between_threads"></a> Sdílení společných prostředků mezi vlákny

> [!NOTE]
>  Podobné informace z hlediska knihovny MFC naleznete v tématu [Multithreading: Programovací tipy](multithreading-programming-tips.md) a [Multithreading: kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md).

Každé vlákno má svůj vlastní zásobníku a zaregistruje vlastní kopii procesoru. Další prostředky, jako jsou soubory, statických dat a paměť haldy jsou sdíleny všemi vlákny v procesu. Vlákna, která používají tyto běžné prostředky musí být synchronizovány. Win32 poskytuje několik způsobů, jak synchronizovat prostředky, včetně semafory, kritické oddíly, události a vzájemně vyloučené přístupy.

Pokud přistupuje více podprocesů statická data, aplikace musí zadat možných konfliktů. Vezměte v úvahu program, kde se aktualizuje statické datové struktury obsahující jedno vlákno *x*,*y* souřadnice pro položky mají být zobrazeny v jiném vlákně. Pokud vlákno aktualizace mění *x* koordinaci a dojde ke zrušení před můžete změnit *y* souřadnice, zobrazení vláken může být naplánována před *y* souřadnice je Aktualizovat. Položka bude zobrazena ve špatném umístění. Tento problém můžete vyhnout použitím semafory řídit přístup ke struktuře.

Objekt mutex (zkratka pro *vzájemně*protokolování přístupu uživatele *ex*clusion) je způsob komunikace mezi vlákny nebo procesy, které jsou navzájem asynchronně. Tato komunikace se obvykle používá ke koordinaci aktivit z více vláken nebo procesy, obvykle řízení přístupu ke sdíleným prostředkům podle zamknutí a odemknutí prostředku. Tento problém vyřešit *x*,*y* problém koordinovat aktualizace, aktualizace vlákna nastaví mutex označující, že je datová struktura používá před provedením aktualizace. Mutex mazal po zpracoval obě souřadnice. Zobrazit vlákna musí čekat vzájemně vyloučený přístup, aby se nezapomnělo před aktualizací zobrazení. Tento proces čeká vzájemně vyloučený přístup se často nazývá blokování na objekt mutex, protože proces se zablokuje a nemůže pokračovat, dokud mutex vymaže.

Bounce.c programu zobrazeného [Ukázkový vícevláknový Program v jazyce C](sample-multithread-c-program.md) používá mutex s názvem `ScreenMutex` koordinovat aktualizace obrazovky. Pokaždé, když je jedno z vláken zobrazení napsat na obrazovku, volá `WaitForSingleObject` spolu s `ScreenMutex` a konstantní NEKONEČNO, která označuje, že `WaitForSingleObject` volání by měly blokovat vzájemně vyloučený přístup a časový limit. Pokud `ScreenMutex` je jasné, čekací funkce nastaví mutex, takže ostatní vlákna nelze ovlivňovat zobrazení a pokračuje v provádění vlákna. V opačném případě vlákno blokuje, dokud mutex vymaže. Po dokončení aktualizace zobrazení vlákna voláním uvolní mutex `ReleaseMutex`.

Zobrazí obrazovku a statická data jsou jenom dvě prostředků vyžaduje pečlivé správy. Například váš program může mít přístup ke stejnému souboru více vláken. Protože jiné vlákno může přesunout ukazatel na soubor, musí každý podproces resetovat ukazatel na soubor před čtením nebo zápisem. Kromě toho každé vlákno musí Ujistěte se, že není přerušeno mezi časem umístí ukazatel a čas, který přistupuje k souboru. Tato vlákna musí použít semafor koordinovat přístup k souboru pomocí "bracketing" každý přístup k souborům s `WaitForSingleObject` a `ReleaseMutex` volání. Následující příklad kódu znázorňuje tento postup:

```
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

##  <a name="_core_thread_stacks"></a> Zásobníky vlákna

Všechny aplikace výchozí prostor v zásobníku je přidělen první vlákno provádění, což se označuje jako vlákno 1. V důsledku toho je nutné zadat, kolik paměti k přidělení pro samostatné zásobníku pro každé další vlákno program potřebuje. Operační systém přiděluje další prostor v zásobníku pro vlákno, v případě potřeby, ale musí určovat výchozí hodnotu.

V první argument `_beginthread` volání je ukazatel `BounceProc` funkce, která spustí vlákna. Druhý argument určuje výchozí velikost zásobníku pro vlákno. Poslední argument je identifikátor, který je předán `BounceProc`. `BounceProc` používá číslo ID pro generátor náhodných čísel, aby vyberte atribut vlákna barvy a zobrazení znaku.

Vlákna, která volání knihovny run-time jazyka C nebo rozhraní API systému Win32 musí poskytovat dostatečné místo zásobníku pro knihovny a rozhraní API funkce, které volají. C `printf` funkce vyžaduje více než 500 bajtů místo v zásobníku a měli byste 2 kB volného místa zásobníku při volání rozhraní API systému Win32 rutin.

Protože každé vlákno má svůj vlastní zásobníku, můžete vyhnout potenciálních kolizí nad datovými položkami použitím jako malý statická data, jako je to možné. Navrhněte program používat automatické proměnné zásobníku pro všechna data, která může být soukromý ve vlákně. Pouze globální proměnné v aplikaci Bounce.c jsou vzájemně vyloučené přístupy nebo proměnné, které nikdy nezmění po jsou inicializovány.

Win32 také poskytuje úložiště Thread Local (TLS) k ukládání dat pro vlákno. Další informace najdete v tématu [vlákna místní úložiště (TLS)](thread-local-storage-tls.md).

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)