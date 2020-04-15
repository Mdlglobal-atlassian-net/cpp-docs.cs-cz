---
title: Knihovny DLL a chování běhové knihovny v jazyce Visual C++
ms.date: 08/19/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
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
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335667"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Knihovny DLL a chování běhové knihovny v jazyce Visual C++

Při vytváření dynamická knihovna (DLL) pomocí Sady Visual Studio, ve výchozím nastavení propojovací program zahrnuje visual c++ run-time knihovny (VCRuntime). Modul VCRuntime obsahuje kód potřebný k inicializaci a ukončení spustitelného souboru C/C++. Při připojení do dll, kód VCRuntime poskytuje interní dll `_DllMainCRTStartup` entry-point funkce volaná, která zpracovává zprávy operačního systému Windows dll připojit nebo odpojit od procesu nebo vlákna. Funkce `_DllMainCRTStartup` provádí základní úkoly, jako je například nastavení zabezpečení vyrovnávací paměti zásobníku, inicializace a ukončení knihovny run-time (C) a volání konstruktorů a destruktorů pro statické a globální objekty. `_DllMainCRTStartup`také volá háček funkce pro jiné knihovny, jako je například WinRT, MFC a ATL provést vlastní inicializaci a ukončení. Bez této inicializace crt a další knihovny, stejně jako statické proměnné, by být ponechány v neinicializovaném stavu. Stejné rutiny interní inicializace a ukončení v běhu VCRuntime se nazývají bez ohledu na to, zda vaše dll používá staticky propojenou crt nebo dynamicky propojenou dll CRT.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Výchozí _DllMainCRTStartup vstupního bodu dll.

V systému Windows mohou všechny knihovny DLL obsahovat volitelnou funkci vstupního bodu, obvykle volanou `DllMain`pro inicializaci i ukončení. To vám dává možnost přidělit nebo uvolnit další zdroje podle potřeby. Systém Windows volá funkci vstupního bodu ve čtyřech situacích: připojení procesu, odpojení procesu, připojení vlákna a odpojení vlákna. Při načtení dll do adresního prostoru procesu, buď při načtení aplikace, která ji používá, nebo když aplikace požaduje DLL za běhu, operační systém vytvoří samostatnou kopii dat DLL. To se nazývá *proces připojit*. *Připojení vlákna* nastane, když proces, ve které je načtena dll, vytvoří nové vlákno. *Odpojení vlákna* nastane, když vlákno ukončí a *odpojit proces* je, když dll již není vyžadována a je uvolněna aplikací. Operační systém provede samostatné volání vstupního bodu dll pro každou z těchto událostí, předávání *argument důvod* pro každý typ události. Například operační ho `DLL_PROCESS_ATTACH` odešle jako *argument důvodu* signál procespřipojit.

Knihovna VCRuntime poskytuje funkci vstupního bodu volanou `_DllMainCRTStartup` pro zpracování výchozích operací inicializace a ukončení. Při připojení procesu `_DllMainCRTStartup` funkce nastaví kontroly zabezpečení vyrovnávací paměti, inicializuje CRT a další knihovny, inicializuje informace typu za běhu, inicializuje a volá konstruktory pro statická a nemístní data, inicializuje `DllMain`místní úložiště podprocesu, inicializuje interní statický čítač pro každý připojení a pak volá uživatelem nebo knihovnou dodávané . Při odpojit proces, funkce prochází těmito kroky v opačném směru. Volání `DllMain`, snížení vnitřní čítač, volá destruktory, volá CRT ukončení funkce a registrované `atexit` funkce a upozorní všechny ostatní knihovny ukončení. Když čítač přílohy přejde na nulu, funkce se vrátí `FALSE` k označení systému Windows, že dll lze uvolnit. Funkce `_DllMainCRTStartup` je také volána během připojení závitu a odpojení závitu. V těchto případech kód VCRuntime nemá žádné další inicializace `DllMain` nebo ukončení samostatně a pouze volání předat zprávu spolu. Pokud `DllMain` `FALSE` se vrátí z procesu `_DllMainCRTStartup` `DllMain` připojit, `DLL_PROCESS_DETACH` signalizace selhání, volání znovu a předá jako *argument důvod,* pak prochází zbytek procesu ukončení.

Při vytváření knihoven DLL v sadě `_DllMainCRTStartup` Visual Studio je výchozí vstupní bod dodaný vcruntime propojen automaticky. Není nutné zadat funkci vstupního bodu pro knihovnu DLL pomocí možnosti propojovacího zařízení [/ENTRY (symbol vstupního bodu).](reference/entry-entry-point-symbol.md)

> [!NOTE]
> I když je možné zadat jinou funkci vstupního bodu pro dll pomocí možnosti /ENTRY: linker, nedoporučujeme ji, `_DllMainCRTStartup` protože vaše funkce vstupního bodu by musela duplikovat vše, co dělá, ve stejném pořadí. VCRuntime poskytuje funkce, které umožňují duplikovat jeho chování. Můžete například volat [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) okamžitě na proces připojit k podpoře [/GS (Buffer kontrola zabezpečení)](reference/gs-buffer-security-check.md) vyrovnávací paměti zaškrtnutí možnost. Můžete volat `_CRT_INIT` funkci, předávání stejné parametry jako vstupní bod funkce, k provedení zbytku funkce inicializace DLL nebo ukončení.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializovat dll

DLL může mít inicializační kód, který musí být spuštěn při načítání dll. Chcete-li provést vlastní funkce inicializace a `_DllMainCRTStartup` ukončení dll, volá funkce volané, `DllMain` které můžete poskytnout. Musíte `DllMain` mít podpis požadovaný pro vstupní bod DLL. Výchozí funkce `_DllMainCRTStartup` vstupního `DllMain` bodu volá pomocí stejných parametrů předaných systémem Windows. Ve výchozím nastavení, pokud `DllMain` neposkytujete funkci, Visual Studio poskytuje jeden `_DllMainCRTStartup` pro vás a propojil ji tak, že má vždy něco volat. To znamená, že pokud není nutné inicializovat dll, není nic zvláštního, co musíte udělat při vytváření dll.

Toto je podpis `DllMain`používaný pro :

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Některé knihovny `DllMain` zabalit funkci za vás. Například v běžné knihovně DLL `CWinApp` knihovny `InitInstance` MFC implementujte funkce objektu a `ExitInstance` členské funkce k provedení inicializace a ukončení vyžadované knihovnou DLL. Další podrobnosti naleznete v části [Inicializovat běžné knihovny DLL knihovny MFC.](#initializing-regular-dlls)

> [!WARNING]
> Existují významná omezení, co můžete bezpečně dělat v vstupním bodě dll. Konkrétní pravidla pro nastavení windows ových api, `DllMain`která nejsou bezpečná pro volání , naleznete v tématu [Obecné doporučené postupy.](/windows/win32/Dlls/dynamic-link-library-best-practices) Pokud potřebujete něco jiného než nejjednodušší inicializaci, proveďte to v inicializační funkci pro dll. Můžete vyžadovat, aby aplikace volaly `DllMain` funkci inicializace po spuštění a před voláním dalších funkcí v dll.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializovat běžné knihovny DLL (jiné než knihovny MFC)

Chcete-li provést vlastní inicializaci v běžných knihovnách DLL (než `_DllMainCRTStartup` knihovny MFC), které používají vstupní `DllMain`bod dodaný v době provádění vcruntime, musí zdrojový kód knihovny DLL obsahovat volanou funkci . Následující kód představuje základní kostru ukazující, jak `DllMain` by definice může vypadat:

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
> Starší dokumentace sady Windows SDK říká, že skutečný název funkce vstupního bodu dll musí být zadán na příkazovém řádku propojovacího programu s parametrem /ENTRY. V sadě Visual Studio není nutné použít možnost /ENTRY, pokud je `DllMain`název funkce vstupního bodu . Ve skutečnosti pokud použijete /ENTRY možnost a pojmenujte `DllMain`funkci vstupního bodu něco jiného než , CRT nezíská inicializována správně, pokud vaše funkce vstupního bodu provede stejné inicializační volání, které `_DllMainCRTStartup` provede.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicializovat běžné knihovny DLL knihovny MFC

Vzhledem k tomu, že `CWinApp` běžné knihovny Knihovny DLL mají objekt, měly by provádět `InitInstance` `ExitInstance` své úlohy inicializace a ukončení ve stejném umístění jako aplikace knihovny MFC: v a členské funkce `CWinApp`odvozené třídy Knihovny DLL. Vzhledem k `DllMain` tomu, že `_DllMainCRTStartup` knihovna MFC poskytuje funkci, která je volána pro `DLL_PROCESS_ATTACH` a `DLL_PROCESS_DETACH`, neměli byste psát vlastní `DllMain` funkci. Funkce zapředpokladu `DllMain` MFC `InitInstance` volá, když je načtena knihovna DLL a volá `ExitInstance` před uvolněním knihovny DLL.

Běžná knihovna MFC DLL může sledovat více vláken voláním [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) a [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) v jeho `InitInstance` funkci. Tyto funkce umožňují dll sledovat data specifická pro vlákno.

V běžné knihovně DLL knihovny MFC, která dynamicky odkazuje na knihovnu MFC, pokud používáte libovolnou podporu knihovny MFC OLE, mfc*version*database (nebo DAO) nebo dfc sockets knihovny MFC, jsou automaticky propojeny ladicí knihovny MFC rozšíření Knihovny DLL, verze MFCD*version*D.dll a*MFCN verze*D.dll (kde je *verze* číslo verze). Je nutné volat jednu z následujících předdefinovaných inicializačních funkcí pro každou z `CWinApp::InitInstance`těchto knihoven DLL, které používáte v běžné knihovně DLL knihovny MFC .

|Typ podpory knihovny MFC|Funkce inicializace pro volání|
|-------------------------|-------------------------------------|
|Knihovna MFC OLE *(verze*MFCO D.dll)|`AfxOleInitModule`|
|Databáze knihovny MFC *(verze*knihovny MFCD D.dll)|`AfxDbInitModule`|
|Sokety knihovny MFC *(verze*MFCN D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicializovat knihovny DLL rozšíření knihovny MFC

Vzhledem k tomu, že knihovny DLL rozšíření knihovny MFC nemají `CWinApp`odvozený objekt (stejně jako `DllMain` běžné knihovny DLL knihovny MFC), měli byste přidat kód inicializace a ukončení do funkce, kterou generuje Průvodce knihovnou DLL knihovny MFC.

Průvodce poskytuje následující kód pro knihovny DLL rozšíření knihovny MFC. V kódu `PROJNAME` je zástupný symbol pro název projektu.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
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

Vytvoření nového `CDynLinkLibrary` objektu během inicializace umožňuje `CRuntimeClass` knihovně MFC rozšíření DLL exportovat objekty nebo prostředky do klientské aplikace.

Pokud budete používat knihovnu DLL rozšíření knihovny MFC z jednoho nebo více běžných knihoven `CDynLinkLibrary` DLL knihovny MFC, je nutné exportovat funkci inicializace, která vytvoří objekt. Tato funkce musí být volána z každého z běžných knihovny DLL knihovny MFC, které používají knihovnu DLL rozšíření knihovny MFC. Vhodné místo pro volání této funkce `InitInstance` inicializace je v členské `CWinApp`funkci běžného objektu DLL knihovny MFC odvozené před použitím libovolné exportované třídy nebo funkce knihovny MFC rozšíření DLL.

V `DllMain` tom, co generuje Průvodce knihovnou DLL knihovny MFC, volání `AfxInitExtensionModule` `CRuntimeClass` zachytí třídy modulu za`COleObjectFactory` běhu (struktury) `CDynLinkLibrary` a jeho objektové továrny (objekty) pro použití při vytvoření objektu. Měli byste zkontrolovat vrácenou hodnotu `AfxInitExtensionModule`; pokud je vrácena `AfxInitExtensionModule`nulová hodnota `DllMain` z , vrátí nulu z funkce.

Pokud bude knihovna DLL rozšíření knihovny MFC explicitně `AfxLoadLibrary` propojena se spustitelným souborem (což znamená spustitelná volání pro propojení s knihovnou DLL), měli byste přidat volání na `AfxTermExtensionModule` . `DLL_PROCESS_DETACH` Tato funkce umožňuje knihovně MFC vyčistit knihovnu DLL rozšíření knihovny MFC, když se každý proces odpojí od knihovny DLL `AfxFreeLibrary` rozšíření knihovny MFC (což se stane, když proces ukončí nebo když je knihovna DLL uvolněna v důsledku volání). Pokud vaše knihovna DLL rozšíření knihovny MFC bude `AfxTermExtensionModule` implicitně propojena s aplikací, volání není nutné.

Aplikace, které explicitně odkazují na knihovny DLL rozšíření knihovny MFC, musí volat `AfxTermExtensionModule` při uvolnění knihovny DLL. Měli by `AfxLoadLibrary` také `AfxFreeLibrary` používat a (namísto `LoadLibrary` `FreeLibrary`Win32 funkce a ) v případě, že aplikace používá více vláken. Použití `AfxLoadLibrary` `AfxFreeLibrary` a zajišťuje, že spuštění a vypnutí kódu, který se spustí při načtení a uvolnění knihovny DLL rozšíření knihovny MFC, nepoškodí globální stav knihovny MFC.

Vzhledem k tomu, že knihovna MFCx0.dll je plně inicializována časem, `DllMain` můžete přidělit paměť a volat funkce knihovny MFC v rámci `DllMain` (na rozdíl od 16bitové verze knihovny MFC).

Rozšíření Knihovny DLL může postarat o `DLL_THREAD_ATTACH` `DLL_THREAD_DETACH` multithreading `DllMain` zpracováním a případy ve funkci. Tyto případy jsou `DllMain` předány při podprocesů připojit a odpojit od Knihovny DLL. Volání [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) při připojení dll umožňuje DLL udržovat indexy místního úložiště vlákna (TLS) pro každé vlákno připojené k DLL.

Všimněte si, že soubor záhlaví Afxdllx.h obsahuje speciální definice pro struktury používané v `AFX_EXTENSION_MODULE` `CDynLinkLibrary`knihovnách DLL rozšíření knihovny MFC, jako je například definice pro a . Tento soubor záhlaví byste měli zahrnout do knihovny DLL přípony knihovny MFC.

> [!NOTE]
> Je důležité, abyste nedefinovali ani nedefinovali žádná `_AFX_NO_XXX` makra v *pch.h* *(stdafx.h* v sadě Visual Studio 2017 a starší). Tato makra existují pouze za účelem kontroly, zda konkrétní cílová platforma tuto funkci podporuje či nikoli. Můžete napsat program pro kontrolu těchto maker `#ifndef _AFX_NO_OLE_SUPPORT`(například ), ale program by nikdy neměl definovat nebo nedefinovat tato makra.

Ukázková inicializační funkce, která zpracovává vícevláknové zpracování je součástí [použití místního úložiště vláken v dynamická knihovna v](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) systému Windows SDK. Všimněte si, že ukázka `LibMain`obsahuje funkci vstupního `DllMain` bodu s názvem , ale měli byste tuto funkci pojmenovat tak, aby fungovala s knihovnami MFC a C run-time.

## <a name="see-also"></a>Viz také

[Vytvoření knihoven DLL c/C++ v sadě Visual Studio](dlls-in-visual-cpp.md)<br/>
[Vstupní bod DllMain](/windows/win32/Dlls/dllmain)<br/>
[Doporučené postupy pro dynamickou knihovnu](/windows/win32/Dlls/dynamic-link-library-best-practices)
