---
title: "Chování běhové knihovny jazyka Visual C++ a knihovny DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75bf84eeaf9277c5cf037c4fa59c28d109d95856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Knihovny DLL a chování běhové knihovny jazyka Visual C++  
  
Při sestavování dynamická knihovna (DLL) pomocí aplikace Visual C++, ve výchozím nastavení, zahrnuje linkeru běhové knihovny jazyka Visual C++ (VCRuntime). VCRuntime obsahuje kód potřebný k inicializaci a ukončit spustitelný soubor C/C++. Při propojení do knihovny DLL, kód VCRuntime poskytuje interní funkce vstupního bodu DLL názvem `_DllMainCRTStartup` , která zpracovává zprávy operačního systému Windows na knihovnu DLL přiřadit nebo odpojení od procesu nebo přístup z více vláken. `_DllMainCRTStartup` Funkce provádí základní úlohy, jako je nastaveno, C běhové knihovny (CRT) inicializace a ukončování zásobníku vyrovnávací paměti zabezpečení a volá konstruktory a destruktory pro statické a globální objekty. `_DllMainCRTStartup`funkce pro jiné knihovny, například WinRT, MFC a knihovny ATL k provedení vlastní inicializace a ukončování háku také volání. Bez této inicializace, CRT a další knihovny, a také statické proměnné zůstane v neinicializovaném stavu. Zda vaše knihovna DLL používá staticky propojené CRT nebo dynamicky propojené knihovny DLL CRT, se nazývají stejné VCRuntime interní inicializace a ukončování rutin.  
  
## <a name="default-dll-entry-point-dllmaincrtstartup"></a>Výchozí knihovny DLL vstupní bod _DllMainCRTStartup  
  
V systému Windows, může obsahovat všechny knihovny DLL funkci vstupního bodu, obvykle s názvem `DllMain`, která je volána pro inicializaci a ukončení. To vám dává příležitost k přidělení nebo uvolnění další prostředky podle potřeby. Windows zavolá funkci vstupní bod v situacích, čtyři: proces připojení, odpojení procesu, vlákno připojení a odpojení přístup z více vláken. Při načítání knihovny DLL do adresního prostoru procesu, při načtení aplikace, která se používá nebo když aplikace požaduje DLL za běhu, operační systém vytvoří samostatnou kopii dat knihovny DLL. To se označuje jako *připojení procesu*. *Vlákno připojit* nastane, když proces knihovnu DLL je načten do vytvoří nové vlákno. *Odebrání vlákna* nastane, když vlákno ukončí, a *odpojení procesu* je, pokud se už nevyžaduje knihovnu DLL a je publikována v rámci aplikace. Operační systém zavolá samostatné vstupní bod knihovny DLL pro každou z těchto událostí, předávání *důvod* argument pro každý typ události. Například operačního systému odešle `DLL_PROCESS_ATTACH` jako *důvod* argument signál proces připojení.  
  
Knihovna VCRuntime představuje vstupní bod funkce volá `_DllMainCRTStartup` zpracovávat výchozí inicializace a ukončování operací. U procesu připojit, `_DllMainCRTStartup` funkce nastaví kontrola zabezpečení vyrovnávací paměti, inicializuje CRT a další knihovny, inicializuje informace běhového typu, inicializuje a volá konstruktory pro statické a jiné než místní data, inicializuje místní úložiště vláken , zvýší interní statické čítač pro každý připojit a potom zavolá uživatelem nebo knihovna zadané `DllMain`. U procesu odpojit, funkce prochází tyto kroky v zpětného. Zavolá `DllMain`, snižuje čítač interní volá destruktory, volání CRT ukončení funkce a zaregistrován `atexit` funkce a upozorní jakékoli jiné knihovny ukončení. Pokud čítač přílohy přejde na hodnotu nula, funkce vrátí hodnotu `FALSE` udávajících Windows, že nelze uvolnit knihovnu DLL. `_DllMainCRTStartup` Funkce je také volána v průběhu vlákno připojení a odpojení přístup z více vláken. V těchto případech kód VCRuntime nemá žádné další inicializace nebo ukončení sama o sobě a právě volá `DllMain` k předání zprávy společně. Pokud `DllMain` vrátí `FALSE` z procesu připojit, signalizaci selhání, `_DllMainCRTStartup` volání `DllMain` znovu a předá `DLL_PROCESS_DETACH` jako *důvod* argument, pak prochází zbytek ukončení procesu.  
  
Při vytváření knihovny DLL v jazyce Visual C++, výchozí vstupní bod `_DllMainCRTStartup` poskytl VCRuntime je automaticky propojena. Není potřeba specifikovat funkci vstupní bod pro knihovny DLL pomocí [/Entry (symbol vstupního bodu)](../build/reference/entry-entry-point-symbol.md) – možnost linkeru.  
  
> [!NOTE]
> Když je možné zadat jinou funkci vstupní bod pro knihovny DLL pomocí/Entry: – možnost linkeru, nedoporučujeme, protože by bylo duplikovat vše, co funkce vstupního bodu, `_DllMainCRTStartup` nemá ve stejném pořadí. VCRuntime poskytuje funkce, které vám umožní duplicitní své chování. Například můžete volat [__security_init_cookie –](../c-runtime-library/reference/security-init-cookie.md) okamžitě proces připojení pro podporu [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md) kontrola možnost vyrovnávací paměti. Můžete volat `_CRT_INIT` funkce, předáte stejné argumenty jako funkce vstupního bodu, provádět zbytek funkcí knihovny DLL inicializace nebo ukončení.  
  
<a name="initializing-a-dll"></a>  
  
## <a name="initialize-a-dll"></a>Inicializace knihovny DLL  
  
Vaše knihovna DLL může mít inicializace kód, který musí být spuštěn při načtení knihovny DLL. V pořadí, které můžete provádět funkce inicializace a ukončování vlastní knihovny DLL `_DllMainCRTStartup` volá funkci s názvem `DllMain` , můžete zadat. Vaše `DllMain` musí mít podpisu, který požaduje pro vstupní bod knihovny DLL. Výchozí vstupní bod funkce `_DllMainCRTStartup` volání `DllMain` pomocí stejné parametry předané v systému Windows. Ve výchozím nastavení, pokud nezadáte `DllMain` funkce, Visual C++ poskytuje za vás a propojuje ho tak, aby `_DllMainCRTStartup` má vždy co volat. To znamená, že pokud nepotřebujete k chybě při inicializaci knihovny DLL, není co speciální, že je nutné provést při vytváření knihovny DLL.  
  
Toto je podpis použitý pro `DllMain`:  
  
```cpp  
#include <windows.h>  
  
extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module 
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```  
  
Některé knihovny zabalení `DllMain` funkce pro vás. Například v běžné knihovny MFC DLL, implementovat `CWinApp` objektu `InitInstance` a `ExitInstance` členské funkce k provedení inicializace a ukončování vyžadují knihovny DLL. Další podrobnosti najdete v tématu [inicializace běžných knihoven MFC DLL](#initializing-regular-dlls) části.  
  
> [!WARNING]
> Na co můžete dělat bezpečně ve vstupním bodě knihovny DLL je důležité omezení. V tématu [obecné osvědčené postupy](https://msdn.microsoft.com/library/windows/desktop/dn633971#general_best_practices) pro konkrétní rozhraní API systému Windows, které jsou unsafe volat v `DllMain`. Pokud budete potřebovat cokoli ale pak nejjednodušší inicializace udělat na inicializační funkce pro knihovnu DLL. Můžete to vyžadovat aplikace pro volání funkce inicializace po `DllMain` má spuštění a před jejich volat jakékoli jiné funkce v knihovně DLL.  
  
<a name="initializing-non-mfc-dlls"></a>  
  
### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializace knihoven DLL běžném provozu (mimo MFC)  
  
K provedení vlastní inicializaci v běžném provozu (mimo MFC) knihovny DLL, které pomocí zadané VCRuntime `_DllMainCRTStartup` vstupní bod vašeho zdrojového kódu knihovny DLL musí obsahovat funkci s názvem `DllMain`. Následující kód představuje základní kostru zobrazující jaké definice `DllMain` může vypadat například:  
  
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
> Starší dokumentace sady Windows SDK říká, že skutečný název funkce vstupního bodu knihovny DLL musí být zadán v linkeru příkazového řádku s parametrem/Entry. S Visual C++, není nutné použít možnost/Entry, pokud je název vstupního bodu funkce `DllMain`. Ve skutečnosti, pokud použijete možnost/ENTRY a název vstupní bod funkce něco jiné než `DllMain`, CRT není správně inicializována Pokud vstupní bod funkce provádí stejné inicializace volání, které `_DllMainCRTStartup` umožňuje.  
  
<a name="initializing-regular-dlls"></a>  
  
### <a name="initialize-regular-mfc-dlls"></a>Inicializovat běžné knihovny MFC DLL  
  
Protože regulární knihovny MFC DLL `CWinApp` objektu, se musí vykonávat úkoly inicializace a ukončování ve stejném umístění jako aplikace knihovny MFC: v `InitInstance` a `ExitInstance` členské funkce knihovnu DLL `CWinApp`-odvozené Třída. Vzhledem k tomu, že poskytuje MFC `DllMain` funkce, která je volána metodou `_DllMainCRTStartup` pro `DLL_PROCESS_ATTACH` a `DLL_PROCESS_DETACH`, neměli psát vlastní `DllMain` funkce. Zadaný MFC `DllMain` volání funkce `InitInstance` při načtení knihovny DLL a volá `ExitInstance` před uvolněním knihovnu DLL.  
  
Běžné knihovny MFC DLL můžete sledovat určité více vláken voláním [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) a [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) v jeho `InitInstance` funkce. Tyto funkce povolit knihovnu DLL sledování dat specifické pro vlákno.  
  
Ve vaší regulární MFC DLL, která propojuje ke knihovně MFC, pokud používáte žádné MFC OLE, MFC databáze (nebo DAO) nebo MFC sokety, respektive ladění MFC – rozšiřující knihovny DLL MFCO*verze*D.dll, MFCD*verze*D.dll a MFCN*verze*D.dll (kde *verze* číslo verze) jsou automaticky propojení v. Pro každou z těchto knihoven DLL, které používáte ve vaší regulární MFC DLL musí volání jednoho z následujících funkcí předdefinované inicializace `CWinApp::InitInstance`.  
  
|Typ Podpora MFC|Funkce inicializace pro volání|  
|-------------------------|-------------------------------------|  
|MFC OLE (MFCO*verze*D.dll)|`AfxOleInitModule`|  
|MFC databáze (MFCD*verze*D.dll)|`AfxDbInitModule`|  
|Sokety MFC (MFCN*verze*D.dll)|`AfxNetInitModule`|  
  
<a name="initializing-extension-dlls"></a>  
  
### <a name="initialize-mfc-extension-dlls"></a>Inicializace MFC – rozšiřující knihovny DLL  
  
Protože MFC – rozšiřující knihovny DLL nemají `CWinApp`-odvozené objektu (jak provádět běžné knihovny MFC DLL), měli byste přidat inicializace a ukončování kód a `DllMain` funkce, která vytváří Průvodce MFC DLL.  
  
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
  
Vytvoření nové `CDynLinkLibrary` objekt během inicializace umožňuje rozšíření MFC DLL export `CRuntimeClass` objekty nebo prostředky do klientské aplikace.  
  
Pokud chcete používat vaše MFC – rozšiřující knihovny DLL z jednoho nebo více regulární knihovny DLL MFC, je nutné exportovat inicializační funkci, která vytvoří `CDynLinkLibrary` objektu. Této funkce musí být volána z každé regulární knihovny MFC DLL použít rozšíření MFC DLL. Příslušné místo pro volání této funkce inicializace je v `InitInstance` – členská funkce regulární MFC DLL `CWinApp`-odvozené objekt před použitím některého z exportovaný třídy nebo funkce MFC DLL rozšíření.  
  
V `DllMain` , Průvodce MFC DLL generuje, volání `AfxInitExtensionModule` zaznamená třídy modulu runtime (`CRuntimeClass` struktury) i jeho objekt Factory (`COleObjectFactory` objekty) pro použijte, když `CDynLinkLibrary` je vytvořen objekt. Vrátí hodnotu, která byste měli zkontrolovat `AfxInitExtensionModule`; Pokud je nulová hodnota vrácená z `AfxInitExtensionModule`, vrátí nula z vaší `DllMain` funkce.  
  
Pokud vaše MFC – rozšiřující knihovny DLL explicitně propojí spustitelný soubor (znamená spustitelné volání `AfxLoadLibrary` na odkaz na knihovnu DLL), měli byste přidat volání `AfxTermExtensionModule` na `DLL_PROCESS_DETACH`. Tato funkce umožňuje knihovně MFC odstranit rozšíření MFC DLL při každém odpojení procesu od rozšíření MFC DLL (který se stane, když proces bude ukončen nebo když je na základě těchto uvolněna z knihovny DLL `AfxFreeLibrary` volání). Pokud vaše MFC – rozšiřující knihovny DLL se implicitně propojena aplikace, volání `AfxTermExtensionModule` není nutné.  
  
Aplikace, které explicitně musí volat odkaz na rozšíření MFC – knihovny DLL `AfxTermExtensionModule` při uvolnění knihovny DLL. Měli by také použít `AfxLoadLibrary` a `AfxFreeLibrary` (místo funkce Win32 `LoadLibrary` a `FreeLibrary`) Pokud aplikace používá více vláken. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který provede, když MFC – rozšiřující knihovny DLL je načítání a uvolňování nejsou poškozeny globální stav MFC.  
  
Vzhledem k tomu, že je knihovna MFCx0.dll plně inicializována čas `DllMain` je volána, můžete přidělit paměť a volání funkce MFC v rámci `DllMain` (na rozdíl od 16bitové verze knihovny MFC).  
  
Rozšiřující knihovny DLL zabýváme více vláken ve zpracování `DLL_THREAD_ATTACH` a `DLL_THREAD_DETACH` případů v `DllMain` funkce. Tyto případy jsou předány `DllMain` při vláken připojení a odpojení z knihovny DLL. Volání metody [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) při připojování knihovny DLL umožňuje umožňuje udržovat přístup z více vláken (TLS) pro místní úložiště indexy pro každé vlákno připojené ke knihovně DLL.  
  
Všimněte si, že soubor hlaviček Afxdllx.h obsahuje zvláštní definice pro struktury používané v MFC rozšiřující knihovny DLL, jako je například definici `AFX_EXTENSION_MODULE` a `CDynLinkLibrary`. Tento soubor hlavičky by měla obsahovat vaše MFC – rozšiřující knihovny DLL.  
  
> [!NOTE]
>  Je důležité, můžete definovat ani žádný z nedefinované `_AFX_NO_XXX` makra v Stdafx.h. Tyto makra existovat jenom pro účely kontroly, jestli konkrétní Cílová platforma podporuje tuto funkci, nebo ne. Můžete napsat váš program Zkontrolujte tyto makra (například `#ifndef _AFX_NO_OLE_SUPPORT`), ale váš program by měl nikdy definovat nebo nedefinované tyto makra.  
  
Ukázka inicializace funkci, která zpracovává více vláken je součástí [pomocí vláken místní úložiště v dynamické knihovně](http://msdn.microsoft.com/library/windows/desktop/ms686997) ve Windows SDK. Všimněte si, že vzorek obsahuje vstupní bod funkce volá `LibMain`, ale tato funkce má název `DllMain` , který bude fungovat s běhové knihovny MFC a C.  
  
## <a name="see-also"></a>Viz také  
  
[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)  
[DllMain vstupního bodu](https://msdn.microsoft.com/library/windows/desktop/ms682583.aspx)  
[Dynamickou knihovnu osvědčené postupy](https://msdn.microsoft.com/library/windows/desktop/dn633971.aspx)  