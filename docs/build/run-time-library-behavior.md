---
title: Knihovny DLL a chování běhové knihovny jazyka Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6606fd65f0f551ca9105c8f9810a75902802334d
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465230"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Knihovny DLL a chování běhové knihovny jazyka Visual C++  
  
Při vytváření dynamické knihovny (DLL) pomocí aplikace Visual C++ ve výchozím nastavení linkeru zahrnuje knihovny run-time jazyka Visual C++ (VCRuntime). VCRuntime obsahuje kód potřebný k inicializaci a ukončit spustitelný soubor jazyka C/C++. V případě propojení do knihovny DLL, kód VCRuntime poskytuje vnitřní funkci vstupního bodu DLL volána `_DllMainCRTStartup` , která zpracovává zprávy operačního systému Windows do knihovny DLL pro připojení nebo odpojení od procesu nebo vlákna. `_DllMainCRTStartup` Funkce provádí základní úlohy, jako je například nastavení jazyka C knihovny run-time (CRT) inicializace a ukončování zabezpečení vyrovnávací paměti zásobníku a volání konstruktorů a destruktorů pro statické a globální objekty. `_DllMainCRTStartup` volání také integrovat funkce pro další knihovny, jako je například WinRT, MFC a ATL provádění vlastní inicializace a ukončování. Bez této inicializace, CRT a dalších knihoven, jakož i statické proměnné zůstane v neinicializovaném stavu. Stejné VCRuntime interní inicializace a ukončování rutin označují, jestli se používají vaše knihovna DLL staticky propojené CRT nebo knihovny DLL dynamicky propojené CRT.  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Výchozí knihovna DLL vstupní bod _DllMainCRTStartup  
  
Ve Windows, můžete všechny knihovny DLL obsahovat funkci vstupního bodu, obvykle nazývaných `DllMain`, která je volána pro inicializaci a ukončení. To vám dává možnost přidělit nebo uvolnit další prostředky podle potřeby. Windows volá funkci vstupního bodu ve čtyřech situacích: připojení procesu, odpojení procesu, vlákna, připojení a odpojení vlákna. Při načtení knihovny DLL do adresového prostoru procesu, při načtení aplikace, která ji používá nebo pokud aplikace vyžaduje knihovnu DLL za běhu, operační systém vytvoří samostatnou kopii dat knihovny DLL. Tento postup se nazývá *připojení procesu*. *Vlákno připojit* nastane, pokud knihovna DLL je načten do procesu vytvoří nové vlákno. *Odpojení vlákna* nastane, pokud vlákno ukončeno, a *odpojení procesu* je, když se už nevyžaduje knihovny DLL a vydání aplikace. Operační systém zavolá samostatné vstupní bod knihovny DLL pro každou z těchto událostí, předávání *důvod* argument pro každý typ události. Příklad: operační systém pošle `DLL_PROCESS_ATTACH` jako *důvod* argument, který signalizuje, že proces připojení.  
  
Knihovna VCRuntime poskytuje funkci vstupního bodu `_DllMainCRTStartup` pro zpracování výchozí inicializace a ukončování operací. V procesu připojení, `_DllMainCRTStartup` funkce nastaví kontroly zabezpečení vyrovnávací paměti, inicializuje CRT a dalších knihoven, inicializuje informace běhového typu, inicializuje a volání konstruktorů pro statické a jiné než místní data, inicializuje místní úložiště vláken , zvýší interní statické čítače pro každé připojení a pak zavolá uživatelem nebo knihovna zadané `DllMain`. V procesu odpojit, funkce prochází tyto kroky v opačném pořadí. Volá `DllMain`, sníží čítač vnitřní volání destruktorů, ukončení volání CRT funkce a zaregistrován `atexit` funkce a upozorní knihovny ukončení. Pokud čítač přílohy sníží na nulu, vrátí funkce `FALSE` udávajících Windows, že knihovna DLL může být uvolněna. `_DllMainCRTStartup` Funkce se také nazývá během vlákno připojení a odpojení vlákna. V těchto případech VCRuntime kód nepodporuje žádné další inicializace nebo ukončení sama o sobě a jen volá `DllMain` k předání zprávy společně. Pokud `DllMain` vrátí `FALSE` z procesu připojení, signalizaci selhání `_DllMainCRTStartup` volání `DllMain` znovu a předává `DLL_PROCESS_DETACH` jako *důvod* argument, pak prochází zbytek ukončení procesu.  
  
Při sestavování knihovny DLL v jazyce Visual C++, výchozí vstupní bod `_DllMainCRTStartup` poskytnutých VCRuntime je automaticky propojena. Není potřeba specifikovat funkci vstupního bodu pro vaši knihovnu DLL pomocí [/Entry (symbol vstupního bodu)](../build/reference/entry-entry-point-symbol.md) – možnost linkeru.  
  
> [!NOTE]
> I když je možné zadat jinou funkci vstupního bodu pro knihovnu DLL pomocí / Entry: – možnost linkeru, nedoporučujeme, protože by duplikovat všechno, co vaši funkci vstupního bodu, který `_DllMainCRTStartup` nemá ve stejném pořadí. VCRuntime poskytuje funkce, které umožňují duplicitní své chování. Například můžete volat [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) okamžitě proces připojení k podpoře [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md) možnost kontroly vyrovnávací paměti. Můžete volat `_CRT_INIT` funkci a předává stejné parametry jako funkci vstupního bodu, provádět zbývající inicializace nebo ukončení funkce knihovny DLL.  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>Inicializace knihovny DLL  
  
Vaše knihovna DLL může mít inicializační kód, který musí být spuštěn při načtení knihovny DLL. Můžete provádět vlastní funkcí knihovny DLL inicializace a ukončování, aby `_DllMainCRTStartup` volá funkci s názvem `DllMain` , který zadáte. Vaše `DllMain` musí mít podpis, vyžaduje se pro vstupní bod knihovny DLL. Funkci vstupního bodu výchozí `_DllMainCRTStartup` volání `DllMain` pomocí stejné parametry předané ve Windows. Ve výchozím nastavení, pokud nezadáte `DllMain` funkce, Visual C++ poskytuje za vás a propojuje ho tak, aby `_DllMainCRTStartup` vždy nabízí něco pro volání. To znamená, že pokud není potřeba vaši knihovnu DLL inicializovat, není nic zvláštního že budete muset udělat při vytváření knihovny DLL.  
  
Toto je podpis použitý pro `DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
Zabalení některé knihovny `DllMain` funkce za vás. Například v běžné knihovny MFC DLL, implementovat `CWinApp` objektu `InitInstance` a `ExitInstance` členské funkce k provedení inicializace a ukončování vyžadované vaší knihovny DLL. Další podrobnosti najdete v tématu [inicializace knihovny DLL MFC regular](#initializing-regular-dlls) oddílu.  
  
> [!WARNING]
> Co můžete dělat bezpečně ve vstupní bod knihovny DLL jsou významné omezení. Zobrazit [obecné osvědčené postupy](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices) pro konkrétní rozhraní API Windows, které nejsou bezpečné volat v `DllMain`. Pokud potřebujete jakoukoli jinou nejjednodušší inicializace potom udělat inicializační funkce pro knihovnu DLL. Můžete vyžadovat, aby aplikace volat funkci inicializace po `DllMain` má spuštění a před jejich volání dalších funkcí v knihovně DLL.  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializace knihovny DLL běžných (non-MFC)  
  
K provádění vlastní inicializace v knihovnách DLL běžných (non-MFC), které používají zadané VCRuntime `_DllMainCRTStartup` vstupní bod, může zdrojový kód knihovny DLL obsahovat funkci s názvem `DllMain`. Následující kód představuje základní kostra zobrazující jaké definici `DllMain` může vypadat například takto:  
  
```cpp  
#include <windows.h>
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason) 
    { 
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```  
  
> [!NOTE]
> Starší dokumentaci k sadě Windows SDK říká, že skutečný název knihovny DLL funkci vstupního bodu musí být zadán v linkeru možnost/Entry příkazového řádku. V jazyce Visual C++ není potřeba použít parametr/Entry, pokud je název vaší funkce vstupního bodu `DllMain`. Ve skutečnosti, pokud používáte parametr/Entry a název vstupního bodu funkce něco jiného než `DllMain`, CRT nelze získat správně inicializován Pokud funkce vstupního bodu provede stejné volání inicializace, která `_DllMainCRTStartup` provede.  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>Inicializovat obvyklé knihovny DLL MFC  
  
Protože regulární knihovny DLL MFC mají `CWinApp` objektu by měla provádějí své úkoly inicializace a ukončování ve stejném umístění jako aplikace knihovny MFC: ve `InitInstance` a `ExitInstance` členské funkce knihovny DLL `CWinApp`-odvozené Třída. Vzhledem k tomu, že knihovna MFC poskytuje `DllMain` funkce, která je volána metodou `_DllMainCRTStartup` pro `DLL_PROCESS_ATTACH` a `DLL_PROCESS_DETACH`, neměli psát vlastní `DllMain` funkce. Pokud MFC `DllMain` volání funkce `InitInstance` při načtení knihovny DLL a volá `ExitInstance` před uvolněním knihovny DLL.  
  
Běžné knihovny MFC DLL může udržovat přehled o více vláken voláním [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) a [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) v jeho `InitInstance` funkce. Tyto funkce umožňují knihovny DLL ke sledování dat specifické pro vlákno.  
  
Ve vaší běžné knihovny MFC DLL, která dynamicky propojuje ke knihovně MFC, pokud používáte žádné MFC OLE, knihovny MFC databáze (nebo rozhraní DAO), nebo soketů knihovny MFC, podporují ladění MFC – rozšiřující knihovny DLL MFCO*verze*D.dll, MFCD*verze*D.dll a MFCN*verze*D.dll (kde *verze* je číslo verze) jsou automaticky propojeny v. Jeden z následujících předdefinovaných inicializační funkce musí zavolat pro každou z těchto knihoven DLL, které používáte ve vaší běžné knihovny MFC DLL `CWinApp::InitInstance`.  
  
|Typ podpory knihovny MFC|Inicializační funkce pro volání|  
|-------------------------|-------------------------------------|  
|MFC OLE (MFCO*verze*D.dll)|`AfxOleInitModule`|  
|Databáze knihovny MFC (MFCD*verze*D.dll)|`AfxDbInitModule`|  
|Soketů knihovny MFC (MFCN*verze*D.dll)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>Inicializace MFC – rozšiřující knihovny DLL  
  
MFC – rozšiřující knihovny DLL nemají `CWinApp`-odvozené objektu (stejně jako běžné knihovny MFC DLL), měli byste přidat kód inicializace a ukončování do `DllMain` funkce, která generuje Průvodce MFC DLL.  
  
 Průvodce poskytuje následující kód pro MFC – rozšiřující knihovny DLL. V kódu `PROJNAME` je zástupný symbol pro název projektu.  
  
```cpp  
#include "stdafx.h"  
#include <afxdllx.h>  
  
#ifdef _DEBUG  
#define new DEBUG_NEW  
#undef THIS_FILE  
static char THIS_FILE[] = __FILE__;  
#endif  
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };  
  
extern "C" int APIENTRY  
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      TRACE0("PROJNAME.DLL Initializing!\n");  
  
      // MFC extension DLL one-time initialization  
      AfxInitExtensionModule(PROJNAMEDLL,   
                                 hInstance);  
  
      // Insert this DLL into the resource chain  
      new CDynLinkLibrary(Dll3DLL);  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      TRACE0("PROJNAME.DLL Terminating!\n");  
   }  
   return 1;   // ok  
}  
```  
  
Vytvoření nového `CDynLinkLibrary` objekt během inicializace umožňuje MFC – rozšiřující knihovny DLL pro export `CRuntimeClass` objekty nebo prostředky do klientské aplikace.  
  
Pokud se chystáte používat vaše MFC – rozšiřující knihovny DLL z jednoho nebo více běžných knihovnách MFC DLL, je nutné exportovat inicializační funkce, která vytvoří `CDynLinkLibrary` objektu. Tato funkce musí být volána ze všech běžných knihovnách MFC DLL použít MFC – rozšiřující knihovny DLL. Je vhodné místo pro volání této funkce inicializace v `InitInstance` členskou funkci běžné knihovny MFC DLL `CWinApp`-odvozenému objektu před použitím některého z exportované třídy nebo funkce MFC DLL rozšíření.  
  
V `DllMain` , Průvodce MFC DLL generuje, volání `AfxInitExtensionModule` zachycuje třídy modulu runtime (`CRuntimeClass` struktury) i jeho objekty pro vytváření objektů (`COleObjectFactory` objektů) pro použití při `CDynLinkLibrary` je vytvořen objekt. Měli byste zkontrolovat návratovou hodnotu `AfxInitExtensionModule`; Pokud není vrácena nulová hodnota z `AfxInitExtensionModule`, vrací nulu z vašich `DllMain` funkce.  
  
Pokud vaše MFC – rozšiřující knihovny DLL se explicitně propojí s spustitelný soubor (to znamená spustitelný soubor volá `AfxLoadLibrary` propojení ke knihovně DLL), měli byste přidat volání `AfxTermExtensionModule` na `DLL_PROCESS_DETACH`. Tato funkce umožňuje vyčistit MFC – rozšiřující knihovny DLL při každém odpojení procesu z MFC – rozšiřující knihovny DLL MFC (který se stane při ukončení procesu nebo pokud kvůli uvolnění knihovny DLL `AfxFreeLibrary` volání). Pokud vaše MFC – rozšiřující knihovny DLL bude implicitně propojené aplikace, volání `AfxTermExtensionModule` není nutné.  
  
Aplikace, které explicitně musí volat odkaz na rozšiřující knihovny DLL MFC `AfxTermExtensionModule` při uvolnění knihovny DLL. Musí taky používat `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkce Win32 `LoadLibrary` a `FreeLibrary`) Pokud aplikace používá více vláken. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který se spustí po MFC – rozšiřující knihovny DLL je načteny nebo uvolněny nejsou poškozeny globální stav knihovny MFC.  
  
Protože knihovny MFCx0.dll je plně inicializován době `DllMain` je volána, můžete přidělit paměť a volání funkcí knihovny MFC v rámci `DllMain` (na rozdíl od 16bitové verze knihovny MFC).  
  
Rozšiřující knihovny DLL zařídit multithreading pomocí manipulace `DLL_THREAD_ATTACH` a `DLL_THREAD_DETACH` případech v `DllMain` funkce. Tyto případy jsou předány `DllMain` při vlákna, připojení a odpojení z knihovny DLL. Volání [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) při připojování knihovny DLL umožňuje udržovat vlákno indexuje místní úložiště (TLS) pro každé vlákno připojené ke knihovně DLL knihovny DLL.  
  
Všimněte si, že soubor hlaviček Afxdllx.h obsahuje speciální definice pro strukturám používaným v rozšiřující knihovny DLL MFC, jako je například definice `AFX_EXTENSION_MODULE` a `CDynLinkLibrary`. V rozšíření MFC DLL, měli byste zahrnout tento soubor hlavičky.  
  
> [!NOTE]
>  Je důležité, že můžete definovat ani nedefinovat některý `_AFX_NO_XXX` makra v souboru Stdafx.h. Tato makra existuje pouze pro účely kontroly, jestli konkrétní Cílová platforma podporuje tuto funkci, nebo ne. Můžete napsat program Zkontrolujte tato makra (například `#ifndef _AFX_NO_OLE_SUPPORT`), ale váš program by nikdy definovat nebo zrušit tato makra.  
  
Funkce inicializace vzorku, který je součástí zpracovává multithreading [pomocí místního úložného prostoru vlákna v knihovně DLL](http://msdn.microsoft.com/library/windows/desktop/ms686997) v sadě Windows SDK. Všimněte si, že ukázky obsahuje funkci vstupního bodu volá `LibMain`, ale tato funkce by měla název `DllMain` tak, že pracuje s knihovny MFC a C za běhu.  
  
## <a name="see-also"></a>Viz také  
  
[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)  
[Zpracování funkce DllMain vstupní bod](/windows/desktop/Dlls/dllmain)  
[Osvědčené postupy dynamická knihovna](/windows/desktop/Dlls/dynamic-link-library-best-practices)  