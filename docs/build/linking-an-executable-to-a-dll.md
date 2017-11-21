---
title: "Propojení spustitelného souboru s knihovnou DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffbb46c562daa213d91892b09e0938d7fd629132
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="link-an-executable-to-a-dll"></a>Propojení spustitelného souboru s knihovnou DLL  
  
Spustitelný soubor, který obsahuje odkazy na (nebo načte) knihovny DLL v jednom ze dvou způsobů:  
  
-   *Implicitní propojení*, kde operační systém knihovnu DLL načte při načtení spustitelný soubor, použití. Spustitelný soubor klienta volá exportovaných funkcí knihovny DLL stejně, jako kdyby byly funkce staticky propojené a obsažené v spustitelný soubor. Implicitní propojení se někdy označuje jako *statické zatížení* nebo *dynamické propojování při načtení*.  
  
-   *Explicitní propojení*, kde na vyžádání v době běhu knihovnu DLL načte, operační systém. Spustitelné soubory, které používá knihovny DLL pomocí explicitní propojení vytvářet volání funkce explicitně zavedení a uvolnění knihovny DLL a přístup k funkce exportované sadou knihovnu DLL. Na rozdíl od volání funkcí staticky propojené knihovny musí spustitelný soubor klienta volat exportovaných funkcí v knihovně DLL prostřednictvím ukazatel na funkci. Explicitní propojení se někdy označuje jako *dynamického zatížení* nebo *spuštění dynamické propojování*.  
  
Spustitelný soubor můžete použít buď propojovací metody pro odkaz na stejnou knihovnu DLL. Kromě toho tyto metody nejsou vzájemně vylučují. jeden spustitelný soubor může implicitně propojit s knihovnou DLL a jiné můžete připojit explicitně.  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>Rozhodování o způsobu vytváření použít  
  
Jestli se má používat implicitní propojení nebo explicitní propojení je architektury rozhodnutí, která je nutno provést pro vaši aplikaci. Existují výhody a nevýhody každé metody.  
  
### <a name="implicit-linking"></a>Implicitní propojení  
  
Implicitní propojení nastane, když kód aplikace volá exportované funkce DLL. Pokud zdrojový kód pro volání spustitelný soubor kompilován nebo sestaven, volání funkce DLL generuje externí odkaz na funkci v kód objektu. Chcete-li vyřešit tento externího odkazu, musí aplikace propojit s poskytovanou tvůrcem knihovny DLL knihovny importu (soubor .lib).  
  
Import knihovny obsahuje jenom kódu načíst knihovnu DLL a implementovat volání funkcí knihovny DLL. Externí funkce hledání v knihovnu importu informuje linkeru, že kód pro tuto funkci je v knihovně DLL. Chcete-li vyřešit externí odkazy na knihovny DLL, linkeru jednoduše přidá informace do spustitelný soubor, který udává systému, kde najít kód knihovny DLL při spouštění procesu.  
  
Při spuštění programu, který obsahuje dynamicky propojenou odkazy systému, používá informace ve spustitelném souboru programu najít požadované knihovny DLL. Pokud nemůže najít knihovnu DLL, systém ukončí proces a zobrazí se dialogové okno, které ohlásí chybu. V systému, jinak hodnota mapuje moduly knihoven DLL do adresního prostoru procesu.  
  
Pokud některé z knihoven DLL, jako má funkci vstupní bod pro kód inicializace a ukončování `DllMain`, operační systém volá funkci. Jeden z parametrů předaných vstupní bod funkce určuje, že je kód, který označuje knihovnu DLL se připojuje k procesu. Pokud funkce vstupního bodu nevrátí hodnotu TRUE, systém ukončí proces a ohlásí chybu.  
  
Nakonec systému upravuje kód spustitelného souboru procesu zadejte počáteční adresy pro funkcí knihovny DLL.  
  
Stejně jako ostatní kódu programu kód knihovny DLL namapovat na adresním prostoru procesu, při spuštění procesu a je načten do paměti pouze v případě potřeby. V důsledku toho `PRELOAD` a `LOADONCALL` atributů kód používá soubory .def řídit načítání v předchozích verzích Windows už mají význam.  
  
### <a name="explicit-linking"></a>Explicitní propojení  
  
Většina aplikací používá implicitní propojení, protože je nejsnažší propojovací metody používat. Existují však situace, kdy je nutné použít explicitní propojení. Zde jsou některé běžné příčiny použití explicitního propojení:  
  
-   Aplikace neví název knihovny DLL, která načte až při spuštění. Aplikace může například získat název knihovny DLL a exportovaných funkcí z konfiguračního souboru při spuštění.  
  
-   Proces, který používá implicitní propojení je ukončen v operačním systému, pokud není nalezena knihovnu DLL při spouštění procesu. Proces, který používá explicitní propojení není v této situaci ukončen a pokuste se zotavit z chyby. Proces může například upozornit uživatele chyby a mít uživatele, zadejte jinou cestu ke knihovně DLL.  
  
-   Proces, který používá implicitní propojení je také ukončen, pokud platí jedna z knihoven DLL je propojena s `DllMain` funkce, která se nezdaří. Proces, který používá explicitní propojení není v této situaci ukončen.  
  
-   Aplikace, která se implicitně odkazuje na mnoho knihoven DLL může být pomalé spustit, protože systém Windows načte všechny knihovny DLL při načtení aplikace. Pro zvýšení výkonu při spuštění aplikace můžete propojit implicitně pouze tyto knihovny DLL požadované ihned po načtení a počkejte, dokud další knihovny DLL požaduje propojení do nich explicitně.  
  
-   Explicitní propojení eliminuje potřebu propojení aplikace pomocí knihovnu importu. Pokud změny v knihovně DLL způsobí změnu export řadových číslovek, aplikace, které používají explicitní propojení, není nutné znovu propojit pokud volají `GetProcAddress` pomocí názvu funkci a není pořadovým číslem, zatímco aplikace, které používají implicitní propojení je nutné znovu propojit na nové knihovny importu.  
  
Zde jsou dvě nebezpečí, které explicitní propojení zajímat:  
  
-   Pokud má knihovna DLL `DllMain` funkce vstupního bodu, operační systém zavolá funkci v kontextu vláken, která volá `LoadLibrary`. Funkce vstupního bodu není volána, pokud knihovnu DLL je již připojen k proces z důvodu předchozích volání `LoadLibrary` který došlo bez odpovídajícího volání `FreeLibrary` funkce. Explicitní propojení může způsobit problémy, pokud používá knihovnu DLL `DllMain` funkce, která se pro každý podproces procesu provést inicializaci, protože vláken, které již existují při `LoadLibrary` (nebo `AfxLoadLibrary`) se nazývá nejsou inicializovány.  
  
-   Pokud se knihovna DLL deklaruje statický rozsah dat jako `__declspec(thread)`, může to způsobit chybu ochrany Pokud explicitně propojený. Po načtení knihovny DLL voláním `LoadLibrary`, způsobí chybu ochrany vždy, když kód odkazuje na tato data. (Statický rozsah dat zahrnuje globální a místní statické položky.) Proto při vytváření knihovny DLL si nepoužívejte úložiště thread-local nebo DLL uživatele informují o potenciální nástrahy dynamického načítání knihovny DLL. Další informace najdete v tématu [používá místní úložiště vláken v dynamické knihovně (Windows SDK)](http://msdn.microsoft.com/library/windows/desktop/ms686997).  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>Postup propojení implicitně s knihovny DLL  
  
Spustitelné soubory klienta používat knihovny DLL pomocí implicitní propojení, musíte získat tyto soubory z zprostředkovatele knihovny DLL:  
  
-   Jeden nebo více hlavičky souborů (souborů .h) obsahující deklarace exportovaná data, funkce nebo třídy jazyka C++ v knihovně DLL. Třídy, funkce a daty exportovanými pomocí knihovny DLL musí všechny označit `__declspec(dllimport)` v záhlaví souboru. Další informace najdete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
-   Importu knihovna pro propojení do spustitelného souboru. Linkeru vytvoří knihovny importu během vytváření knihovny DLL. Další informace najdete v tématu [. Soubory LIB](../build/reference/dot-lib-files-as-linker-input.md).  
  
-   Skutečný soubor knihovny DLL.  
  
Použití knihovny DLL pomocí implicitní propojení, spustitelný soubor musí obsahovat záhlaví soubory, které deklarovat data, funkce nebo třídy C++ exportovaná knihovnou DLL v každé zdrojový soubor, který obsahuje volání exportovaná data, funkce a třídy. Z hlediska kódování volání exportovaných funkcí jsou stejně jako jakékoli jiné volání funkce.  
  
Chcete-li vytvořit volání spustitelný soubor, musí propojit s knihovny importu. Pokud používáte externí soubor pravidel nebo sestavení system, zadejte název souboru knihovny importu, kde můžete seznam další soubory objektu (.obj) nebo knihovny, které propojení.  
  
Operační systém musí být při volání spustitelný soubor načte, se najít soubor knihovny DLL. To znamená, že musí aplikaci nasadit nebo ověřte existenci knihovnu DLL, při instalaci aplikace.   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>Postup propojení explicitně s knihovny DLL  
  
Chcete-li používat knihovny DLL pomocí explicitní propojení, aplikace provést volání funkce, aby v době běhu explicitně načíst knihovnu DLL. Explicitní odkaz na knihovnu DLL, musí aplikace:  
  
-   Volání [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx`, nebo podobné funkce, která se načíst knihovnu DLL a získat popisovač modulu.  
  
-   Volání [GetProcAddress](getprocaddress.md) získat ukazatel funkce na každý exportované funkce, která volá aplikaci. Protože aplikace volání funkcí knihovny DLL prostřednictvím ukazatele, kompilátor negeneruje externí odkazy, takže není nutné propojení s knihovnu importu. Ale musíte mít `typedef` nebo `using` příkaz, který definuje podpis volání exportovaných funkcí, které volat.   
  
-   Volání [FreeLibrary](freelibrary-and-afxfreelibrary.md) po dokončení práce s knihovnou DLL.  
  
Například tato ukázka funkce volá `LoadLibrary` načtení knihovny DLL s názvem "MyDLL", zavolá `GetProcAddress` získat ukazatel na funkci s názvem "DLLFunc1" volá funkci a uloží výsledek a pak zavolá `FreeLibrary` se uvolnit knihovnu DLL. 
  
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
  
Na rozdíl od v tomto příkladu, ve většině případů byste měli zavolat `LoadLibrary` a `FreeLibrary` pouze jednou v aplikaci pro danou knihovny DLL, zejména pokud chcete zavolat víc funkcí v knihovně DLL nebo volání knihovny DLL funkce opakovaně.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Práce s importovanými knihovnami a exportovanými soubory](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Vyhledávací cesta používaná systémem Windows k nalezení knihovny DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)