---
title: Propojení spustitelného souboru s knihovnou DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9641545721776530ccf09a5a1ea99485f510265
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465151"
---
# <a name="link-an-executable-to-a-dll"></a>Propojení spustitelného souboru s knihovnou DLL  
  
Spustitelný soubor odkazuje na (nebo načítá) knihovnu DLL jedním ze dvou způsobů:  
  
-   *Implicitní propojení*, kdy operační systém načte knihovnu DLL při načtení spustitelného souboru jeho použití. Klientský spustitelný soubor volá exportované funkce DLL tak, jako kdyby byly funkce staticky propojené a obsažené ve spustitelném souboru. Implicitní propojení se někdy označuje jako *statické načítání* nebo *dynamické propojování během načítání*.  
  
-   *Explicitní propojení*, kdy operační systém načte knihovnu DLL na vyžádání za běhu. Spustitelný soubor, který používá knihovnu DLL explicitním propojením musí volat funkce pro explicitní načtení a uvolnění knihoven DLL a pro přístup k funkcí exportovaných knihovnou DLL. Na rozdíl od volání funkcí v staticky propojené knihovny musí klientský spustitelný soubor volat exportované funkce v knihovně DLL pomocí ukazatele na funkci. Explicitní propojení se někdy označuje jako *dynamického zatížení* nebo *dynamické propojení za běhu*.  
  
Spustitelný soubor můžete použít jakoukoli metodou propojení odkaz na stejnou knihovnu DLL. Kromě toho tyto metody se vzájemně nevylučují; jeden spustitelný soubor se může implicitně propojit s knihovnou DLL a jiný může připojit explicitně.  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>Určit, kterou propojovací metodu použít  
  
Jestli se má použít implicitní nebo explicitní propojení je rozhodnutí o architektuře, které musíte provést pro vaši aplikaci. Existují výhody a nevýhody každé metody.  
  
### <a name="implicit-linking"></a>Implicitní propojení  
  
Implicitní propojení nastane, pokud kód aplikace volá exportované funkce DLL. Pokud zdrojový kód pro volání spustitelný soubor je zkompilován nebo sestaven, volání funkce DLL generuje externí odkaz na funkci v kódu objektu. Chcete-li vyřešit tento vnější odkaz, aplikaci je třeba propojit s knihovnou importu (soubor .lib) poskytovanou tvůrcem knihovny DLL.  
  
Knihovna importu obsahuje pouze kód načíst knihovnu DLL a provádět volání funkcí v knihovně DLL. Externí funkce hledání v knihovně importu informuje linkeru, že kód pro tuto funkci je v knihovně DLL. Překládat externí odkazy na knihovny DLL, linker jednoduše přidá informace do spustitelného souboru, který říká systému, kde najdete kód knihovny DLL při spuštění procesu.  
  
Při spuštění systému program, který obsahuje dynamicky propojenou odkazy, používá k vyhledání požadovaných knihoven DLL informace do spustitelného souboru programu. Pokud nemůže najít knihovnu DLL, systém ukončí proces a zobrazí dialogové okno, které se ohlásí chybu. V opačném případě systém mapuje moduly knihoven DLL do adresního prostoru procesu.  
  
Pokud některý z knihovny DLL, jako má funkci vstupního bodu pro kód inicializace a ukončování `DllMain`, operační systém zavolá funkci. Jeden z parametrů předaných funkci vstupního bodu určuje kód, který označuje, knihovna DLL je připojování k procesu. Pokud funkce vstupního bodu nevrací hodnotu TRUE, systém ukončí proces a ohlásí chybu.  
  
Nakonec systém změní spustitelný kód procesu zadejte počáteční adresy pro funkce knihovny DLL.  
  
Stejně jako ostatní kódu programu je namapována kód knihovny DLL do adresového prostoru procesu při spuštění procesu a je načten do paměti pouze v případě potřeby. V důsledku toho `PRELOAD` a `LOADONCALL` atributy kódu používá .def soubory na ovládací prvek načítání v předchozích verzích Windows už mají význam.  
  
### <a name="explicit-linking"></a>Explicitní propojení  
  
Většina aplikací používá implicitní propojení, protože je nejsnažší propojovací metodu použít. Existují však situace, kdy je nutné použít explicitní propojení. Tady jsou některé běžné důvody pro použití explicitní propojení:  
  
-   Aplikace neví název knihovny DLL, která načte až do spuštění. Aplikace může například získat název knihovny DLL a exportované funkce v konfiguračním souboru při spuštění.  
  
-   Proces, který používá implicitní propojení bude ukončeno podle operačního systému při spouštění procesu nebyla nalezena knihovna DLL. Proces, který používá explicitní propojení není ukončený v této situaci a může pokusit obnovit z chyby. Například proces by mohl oznámit uživateli chybu a požádat uživatele o určení jiné cesty ke knihovně DLL.  
  
-   Proces, který používá implicitní propojení se také ukončí, pokud některý z knihovny DLL je propojena s `DllMain` funkce, která se nezdaří. V této situaci není ukončen proces, který používá explicitní propojení.  
  
-   Aplikace, která implicitně obsahuje odkazy na mnoho knihoven DLL může trvat dlouho. spustit, protože Windows načte všechny knihovny DLL při načtení aplikace. Pokud chcete zlepšit výkon při spouštění, můžete aplikace implicitní propojení pouze na tyto knihovny DLL požadované bezprostředně po načtení a počkat, až do další knihovny DLL je potřeba vytvořit na ně explicitně propojení.  
  
-   Explicitní propojení se eliminuje potřeba propojit aplikaci s použitím knihovny importu. Pokud změny v knihovně DLL způsobí změnu export řadových číslovek, aplikace, které používají explicitní propojení, není nutné znovu připojit, pokud volají `GetProcAddress` pomocí názvu funkce a ne pořadové číslo, že aplikace, které používají implicitní propojení musíte znovu připojit k Nová knihovna importu.  
  
Tady jsou dvě nebezpečí explicitní propojení zajímat:  
  
-   Pokud má knihovna DLL `DllMain` funkci vstupního bodu, operační systém zavolá funkci v kontextu vlákna, která se nazývá `LoadLibrary`. Funkce vstupního bodu není volána, pokud knihovna DLL již připojena k procesu z důvodu předchozího volání `LoadLibrary` , který má určitá bez odpovídajícího volání `FreeLibrary` funkce. Explicitní propojení může způsobit potíže, pokud používá knihovnu DLL `DllMain` funkce, která se pro každý podproces procesu provést inicializaci, protože vláken, která již existuje. při `LoadLibrary` (nebo `AfxLoadLibrary`) se nazývá nejsou inicializovány.  
  
-   Pokud knihovna DLL deklaruje statický rozsah dat jako `__declspec(thread)`, pokud explicitně propojený může způsobit chybu ochrany. Po načtení knihovny DLL voláním `LoadLibrary`, způsobí chybu ochrany pokaždé, když se kód odkazuje na tato data. (Statický rozsah data obsahují globální a místní statických položek.) Proto při vytváření knihovny DLL si místní úložiště vláken nepoužívejte nebo knihovny DLL uživatele informují o potenciálních problémech dynamicky načítání knihovny DLL. Další informace najdete v tématu [dynamická knihovna (Windows SDK) v místním úložišti vláken](http://msdn.microsoft.com/library/windows/desktop/ms686997).  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>Jak implicitní propojení s knihovnou DLL  
  
Pomocí implicitní propojení s knihovnou DLL, musíte získat spustitelné soubory klienta tyto soubory z knihovny DLL zprostředkovatele:  
  
-   Jeden nebo více soubory hlaviček (.h souborů), které obsahují deklarace exportovaná data, funkce a/nebo třídy jazyka C++ v knihovně DLL. Třídy, funkce a data exportovaná knihovnou DLL musí všechny být označeny `__declspec(dllimport)` v hlavičkovém souboru. Další informace najdete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
-   Knihovnu importu propojit do spustitelného souboru. Propojovací program vytvoří knihovnu importu při vytváření knihovny DLL. Další informace najdete v tématu [. Soubory knihovny LIB](../build/reference/dot-lib-files-as-linker-input.md).  
  
-   Skutečný soubor knihovny DLL.  
  
Pomocí implicitní propojení s knihovnou DLL, spustitelný soubor musí obsahovat soubory hlaviček, které deklarují data, funkce nebo exportovaných knihovnou DLL v každý zdrojový soubor, který obsahuje volání do třídy exportovaná data, funkce a třídy jazyka C++. Z hlediska kódování volání exportovaných funkcí jsou stejně jako ostatní volání funkce.  
  
K vytvoření volání spustitelný soubor, je třeba propojit s importovanou knihovnou. Pokud používáte externí soubor pravidel nebo sestavovací systém, zadejte název souboru knihovny importu, kde můžete seznam dalších souborů objektů (.obj) nebo knihovny, které můžete propojit.  
  
Operační systém musí být schopen najít soubor knihovny DLL při načtení volání spustitelný soubor. To znamená, že musí aplikaci nasadit nebo ověřování existence knihovny DLL při instalaci vaší aplikace.   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>Jak explicitní propojení ke knihovně DLL  
  
Pomocí explicitní propojení s knihovnou DLL, musí aplikace provést volání funkce, aby explicitně načíst knihovnu DLL v době běhu. Pro explicitní propojení ke knihovně DLL, musí aplikace:  
  
-   Volání [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx`, nebo podobné funkce, která se načíst knihovnu DLL a získat popisovač modulu.  
  
-   Volání [GetProcAddress](getprocaddress.md) získání ukazatele na funkci na každý exportované funkce, která volá aplikaci. Protože aplikace volat funkce knihovny DLL prostřednictvím ukazatele, kompilátor negeneruje externí odkazy, takže není nutné k propojení s knihovnou importu. Ale musíte mít `typedef` nebo `using` příkaz, který definuje podpis volání exportovaných funkcí, které můžete volat.   
  
-   Volání [FreeLibrary](freelibrary-and-afxfreelibrary.md) až budete hotovi s knihovnou DLL.  
  
Například volání této ukázkové funkce `LoadLibrary` načtení knihovny DLL s názvem "MyDLL" volá `GetProcAddress` získat ukazatel na funkci s názvem "DLLFunc1", volá funkci a uloží výsledek a pak zavolá `FreeLibrary` uvolnit knihovnu DLL. 
  
```C  
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);  

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)  
{
    HINSTANCE hDLL;               // Handle to DLL  
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
    HRESULT hrReturnVal;  
      
    hDLL = LoadLibrary("MyDLL");  
    if (NULL != hDLL)  
    {  
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");  
        if (NULL != lpfnDllFunc1)  
        {  
            // call the function  
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);  
        }  
        else  
        {  
            // report the error  
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;  
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }  
    return hrReturnVal;
}
```  
  
Na rozdíl od v tomto příkladu, ve většině případů byste měli volat `LoadLibrary` a `FreeLibrary` opakovaně funguje pouze jednou v aplikaci pro dané knihovny DLL, zejména v případě, že se chystáte volání více funkcí v knihovně DLL nebo volání knihovny DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?  
  
-   [Práce s knihovnami importu a soubory exportu](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Pořadí hledání knihoven DLL](/windows/desktop/Dlls/dynamic-link-library-search-order)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)