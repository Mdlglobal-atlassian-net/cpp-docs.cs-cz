---
title: Multithreading s použitím jazyka C a prostředí Win32
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422120"
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading s použitím jazyka C a prostředí Win32

Microsoft C/C++ COMPILER (MSVC) poskytuje podporu pro vytváření aplikací s více vlákny. Zvažte použití více než jednoho vlákna, pokud vaše aplikace potřebuje provést náročné operace, které by mohly způsobit, že uživatelské rozhraní přestane reagovat.

V MSVC existuje několik způsobů, jak programovat s více vlákny: můžete použít C++/WinRT a knihovnu prostředí Windows Runtime, knihovnu Microsoft Foundation Class (MFC), C++třídu/CLI a modul runtime .NET nebo knihovnu run-time jazyka C a Win32 API. Tento článek se týká multithreadingu v jazyce C. Příklad kódu naleznete v tématu [Ukázka vícevláknového programu v jazyce C](sample-multithread-c-program.md).

## <a name="multithread-programs"></a>Programy s více vlákny

Vlákno je v podstatě cesta provádění prostřednictvím programu. Je to také nejmenší jednotka provádění těchto plánů Win32. Vlákno se skládá ze zásobníku, stavu registrů CPU a záznamu v seznamu spuštění plánovače systému. Každé vlákno sdílí všechny prostředky procesu.

Proces se skládá z jednoho nebo více vláken a kódu, dat a dalších prostředků programu v paměti. Typickými prostředky programu jsou otevřené soubory, semafory a dynamicky přidělená paměť. Program se spustí, když Plánovač systému poskytne jeden z jeho řídicího prvku pro spuštění vlákna. Plánovač určuje, která vlákna by se měla spouštět a kdy se mají spustit. Vlákna s nižší prioritou můžou počkat, zatímco vlákna s vyšší prioritou dokončí jejich úkoly. V počítačích s více procesory může plánovač přesunout jednotlivá vlákna do různých procesorů a vyrovnávat zatížení procesoru.

Každé vlákno v procesu funguje nezávisle. Pokud je nevidíte navzájem, vlákna se spouštějí jednotlivě a nevědí o ostatních vláknech v procesu. Vlákna sdílející běžné prostředky však musí koordinovat svou práci pomocí semaforů nebo jiné metody komunikace mezi procesy. Další informace o synchronizaci vláken naleznete v tématu [napsání vícevláknového programu Win32](#writing-a-multithreaded-win32-program).

## <a name="library-support-for-multithreading"></a>Podpora knihovny pro multithreading

Všechny verze CRT teď podporují multithreading, s výjimkou neuzamykání verzí některých funkcí. Další informace najdete v tématu [výkon vícevláknových knihoven](../c-runtime-library/multithreaded-libraries-performance.md). Informace o verzích CRT dostupných pro propojení s vaším kódem naleznete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

## <a name="include-files-for-multithreading"></a>Zahrnuté soubory pro multithreading

Standardní CRT vložené soubory deklaruje funkce běhové knihovny jazyka C, jak jsou implementovány v knihovnách. Pokud vaše možnosti kompilátoru určují [__fastcall nebo __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md) konvence volání, kompilátor předpokládá, že všechny funkce by měly být volány pomocí konvence volání registrace. Funkce běhové knihovny používá konvenci volání jazyka C a deklarace ve standardních vložených souborech říká kompilátoru, aby vygeneroval správné externí odkazy na tyto funkce.

## <a name="crt-functions-for-thread-control"></a>Funkce CRT pro řízení vláken

Všechny programy Win32 mají alespoň jedno vlákno. Jakékoli vlákno může vytvořit další vlákna. Vlákno může dokončit svou práci rychle a pak ukončit nebo může zůstat aktivní po dobu života programu.

Knihovny CRT poskytují následující funkce pro vytvoření vlákna a ukončení: [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md), [_endthread a _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).

Funkce `_beginthread` a `_beginthreadex` vytvoří nové vlákno a vrátí identifikátor vlákna, pokud je operace úspěšná. Vlákno se automaticky ukončí, pokud dokončí provádění. Nebo se může ukončit s voláním `_endthread` nebo `_endthreadex`.

> [!NOTE]
> Pokud zavoláte rutiny run-time jazyka C z programu sestaveného pomocí Libcmt. lib, je nutné spustit vlákna pomocí funkce `_beginthread` nebo `_beginthreadex`. Nepoužívejte funkce Win32 `ExitThread` a `CreateThread`. Použití `SuspendThread` může vést k zablokování v případě, že více než jedno vlákno zablokuje čekání na jeho přístup ke struktuře dat za běhu v jazyce C.

### <a name="_core_the__beginthread_function"></a>Funkce _beginthread a _beginthreadex

Funkce `_beginthread` a `_beginthreadex` vytvoří nové vlákno. Vlákno sdílí kód a datové segmenty procesu s ostatními vlákny v procesu, ale má své vlastní jedinečné hodnoty registru, prostor zásobníku a aktuální adresu instrukcí. Systém dává každému vláknu čas procesoru, aby se všechna vlákna v procesu mohla spouštět souběžně.

`_beginthread` a `_beginthreadex` jsou podobné funkci [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) v Win32 API, ale mají tyto rozdíly:

- Inicializují určité proměnné knihovny run-time jazyka C. To je důležité pouze v případě, že použijete knihovnu run-time jazyka C ve vašich vláknech.

- `CreateThread` pomáhá zajistit kontrolu nad atributy zabezpečení. Pomocí této funkce můžete spustit vlákno v pozastaveném stavu.

`_beginthread` a `_beginthreadex` vrátí popisovač do nového vlákna, pokud došlo k chybě, nebo kód chyby, pokud došlo k chybě.

### <a name="_core_the__endthread_function"></a>Funkce _endthread a _endthreadex

Funkce [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) ukončí vlákno vytvořené pomocí `_beginthread` (a podobně `_endthreadex` ukončí vlákno vytvořené `_beginthreadex`). Vlákna se po dokončení automaticky ukončí. `_endthread` a `_endthreadex` jsou užitečné pro podmíněné ukončení v rámci vlákna. Vlákno vyhrazené pro zpracování komunikace může být například ukončeno, pokud není schopno získat kontrolu nad komunikačním portem.

## <a name="writing-a-multithreaded-win32-program"></a>Psaní programů s více vlákny pro prostředí Win32

Při psaní programu s více vlákny je nutné koordinovat jejich chování a [používání prostředků programu](#_core_sharing_common_resources_between_threads). Také se ujistěte, že každé vlákno obdrží [vlastní zásobník](#_core_thread_stacks).

### <a name="_core_sharing_common_resources_between_threads"></a>Sdílení společných prostředků mezi vlákny

> [!NOTE]
> Podobnou diskusi z pohledu knihovny MFC naleznete v tématu [Multithreading: Tipy pro programování](multithreading-programming-tips.md) a [Multithreading: Kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md).

Každé vlákno má vlastní zásobník a vlastní kopii registrů procesoru. Další prostředky, jako jsou soubory, statická data a paměť haldy, jsou sdíleny všemi vlákny v procesu. Vlákna používající tyto běžné prostředky musí být synchronizovaná. Win32 nabízí několik způsobů, jak synchronizovat prostředky, jako jsou semafory, kritické oddíly, události a mutexy.

Pokud více vláken přistupuje k statickým datům, váš program musí poskytovat možné konflikty prostředků. Vezměte v úvahu program, ve kterém jedno vlákno aktualizuje statickou datovou strukturu obsahující souřadnice *x*,*y* pro položky, které mají být zobrazeny v jiném vlákně. Pokud vlákno aktualizace změní souřadnici *x* a je přerušeno předtím, než může změnit souřadnici *y* , vlákno zobrazení může být naplánováno před aktualizací souřadnic *y* . Položka se zobrazí v nesprávném umístění. Tomuto problému se můžete vyhnout použitím semaforů k řízení přístupu ke struktuře.

Mutex (krátký pro *Mut*protokolování přístupu uživatele *ex*clusion) je způsob, jak komunikovat mezi vlákny nebo procesy, které jsou spouštěny asynchronně. Tato komunikace se dá použít ke koordinaci aktivit více vláken nebo procesů, obvykle řízení přístupu ke sdílenému prostředku uzamčením a odemknutím prostředku. Aby bylo možné tento problém s aktualizací souřadnic *x*,*y* vyřešit, vlákno aktualizace nastaví mutex, který značí, že se datová struktura používá před provedením aktualizace. Odstraní mutex po zpracování obou souřadnic. Vlákno zobrazení musí před aktualizací zobrazení počkat na vymazání objektu mutex. Tento proces čekání na mutex se často označuje jako *blokující* na mutexu, protože proces je zablokován a nemůže pokračovat, dokud se neodstraní mutex.

Program odraz. c zobrazený v [ukázce vícevláknového programu](sample-multithread-c-program.md) v jazyce c používá k koordinaci aktualizací obrazovky mutex s názvem `ScreenMutex`. Pokaždé, když je jedno z vláken zobrazení připravené k zápisu na obrazovku, volá `WaitForSingleObject` s popisovačem `ScreenMutex` a konstantou nekonečné k označení toho, že by volání `WaitForSingleObject` mělo blokovat na mutex a nikoli časový limit. Pokud je `ScreenMutex` jasné, funkce Wait nastaví mutex tak, aby ostatní vlákna nebránila zobrazení a pokračuje v provádění vlákna. V opačném případě vlákno zablokuje, dokud se neodstraní mutex. Když vlákno dokončí aktualizaci zobrazení, uvolní mutex voláním `ReleaseMutex`.

Obrazovky a statická data jsou pouze dva prostředky vyžadující pečlivé řízení. Například váš program může mít více vláken, která přistupují ke stejnému souboru. Protože jiné vlákno mohl přesunout ukazatel na soubor, musí každé vlákno před čtením nebo zápisem obnovit ukazatel na soubor. Kromě toho musí každé vlákno zajistit, že není přerušeno mezi časem umístění ukazatele a časem, který tento soubor přistupuje. Tato vlákna by měla pomocí semaforu koordinovat přístup k souboru tím, že jednotlivé soubory zastupují do závorek pomocí `WaitForSingleObject` a `ReleaseMutex` volání. Následující příklad kódu znázorňuje tuto techniku:

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>Zásobníky vláken

Veškeré výchozí místo v zásobníku aplikace je přiděleno prvnímu vláknu spuštění, které se označuje jako vlákno 1. V důsledku toho musíte zadat, kolik paměti se má přidělit samostatnému zásobníku pro každé další vlákno, které program potřebuje. Operační systém přiděluje další prostor v zásobníku pro vlákno, je-li to nutné, ale je nutné zadat výchozí hodnotu.

První argument ve volání `_beginthread` je ukazatel na funkci `BounceProc`, která spouští vlákna. Druhý argument určuje výchozí velikost zásobníku pro vlákno. Poslední argument je číslo ID, které je předáno do `BounceProc`. `BounceProc` používá ID pro počáteční generátor náhodných čísel a výběr atributu barvy vlákna a zobrazeného znaku.

Vlákna, která provádějí volání do běhové knihovny jazyka C nebo do Win32 API, musí umožňovat dostatečné místo v zásobníku pro knihovnu a funkce rozhraní API, které volají. Funkce `printf` jazyka C vyžaduje více než 500 bajtů místa v zásobníku a při volání rutin Win32 API byste měli mít k dispozici 2K bajty místa v zásobníku.

Vzhledem k tomu, že každé vlákno má vlastní zásobník, můžete se vyhnout potenciálním kolizím nad datovými položkami pomocí co nejmenšího množství statických dat. Navrhněte svůj program pro použití automatických proměnných zásobníku pro všechna data, která mohou být pro vlákno soukromá. Jediné globální proměnné v programu odraz. c jsou buď mutexy, nebo proměnné, které se po inicializaci nikdy nemění.

Win32 také poskytuje místní úložiště (TLS) pro ukládání dat jednotlivých vláken. Další informace najdete v tématu [místní úložiště vláken (TLS)](thread-local-storage-tls.md).

## <a name="avoiding-problem-areas-with-multithread-programs"></a>Obcházení problémových oblastí pomocí programů s více vlákny

Existuje několik problémů, se kterými se můžete setkat při vytváření, propojování nebo spouštění vícevláknového programu v jazyce C. Některé z nejběžnějších problémů jsou popsány v následující tabulce. (Podobná diskuze z pohledu knihovny MFC naleznete v tématu [Multithreading: programovací tipy](multithreading-programming-tips.md).)

|Problém|Pravděpodobná příčina|
|-------------|--------------------|
|Zobrazí se okno se zprávou, že váš program způsobil narušení ochrany.|Mnoho chyb programování v systému Win32 způsobuje narušení ochrany. Běžnou příčinou narušení ochrany je nepřímá přiřazování dat k ukazatelům s hodnotou null. Vzhledem k tomu, že se program pokusí získat přístup k paměti, která k němu nepatří, dojde k narušení ochrany.<br /><br /> Snadný způsob, jak zjistit příčinu narušení ochrany, je kompilovat program pomocí ladicích informací a pak ho spustit prostřednictvím ladicího programu v prostředí sady Visual Studio. Pokud dojde k chybě ochrany, systém Windows přenáší řízení ladicímu programu a kurzor je umístěn na řádku, který způsobil problém.|
|Program vygeneruje množství chyb kompilace a propojení.|Můžete eliminovat mnoho potenciálních problémů tím, že nastavíte úroveň upozornění kompilátoru na jednu z jejich nejvyšší hodnoty a heeding varovné zprávy. Pomocí možností úrovně upozornění úrovně 3 nebo úrovně 4 můžete detekovat neúmyslné převody dat, chybějící prototypy funkcí a používat funkce, které nejsou standardem ANSI.|

## <a name="see-also"></a>Viz také

[Podpora multithreadingu pro starší kód (vizuální C++)](multithreading-support-for-older-code-visual-cpp.md)\
[Ukázkový vícevláknový program v jazyce C](sample-multithread-c-program.md)\
[Místní úložiště vláken (TLS)](thread-local-storage-tls.md)\
[Souběžné a asynchronní operace s C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency)\
[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
