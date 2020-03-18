---
title: Knihovny DLL a C++ chování běhové knihovny jazyka Visual runtime
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
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417311"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Knihovny DLL a C++ chování běhové knihovny jazyka Visual runtime

Když vytváříte dynamickou knihovnu (DLL) pomocí sady Visual Studio, ve výchozím nastavení linker zahrnuje Visual C++ Run-Time Library (VCRuntime). VCRuntime obsahuje kód potřebný k inicializaci a ukončení spustitelného souboru CC++ /. Při propojení s knihovnou DLL poskytuje kód VCRuntime interní funkci vstupního bodu knihovny DLL s názvem `_DllMainCRTStartup`, která zpracovává zprávy operačního systému Windows do knihovny DLL pro připojení k procesu nebo vláknu nebo k jejich odpojení. Funkce `_DllMainCRTStartup` provádí základní úlohy, jako je nastavení zabezpečení vyrovnávací paměti zásobníku, inicializace a ukončení knihovny run-time Library (CRT) a volání konstruktorů a destruktorů pro statické a globální objekty. `_DllMainCRTStartup` také volá funkce připojení pro jiné knihovny, jako je WinRT, MFC a ATL, aby prováděly svou vlastní inicializaci a ukončení. Bez této inicializace by CRT a jiné knihovny, stejně jako statické proměnné, byly ponechány v neinicializovaném stavu. Stejné VCRuntime interní inicializace a rutiny ukončení jsou volány, pokud vaše knihovna DLL používá staticky propojenou CRT nebo dynamicky propojenou knihovnu CRT DLL.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Výchozí vstupní bod knihovny DLL _DllMainCRTStartup

V systému Windows všechny knihovny DLL mohou obsahovat volitelnou funkci vstupního bodu, která se obvykle označuje jako `DllMain`, která je volána pro inicializaci i ukončení. Získáte tak možnost přidělit nebo uvolnit další prostředky podle potřeby. Systém Windows volá funkci vstupního bodu ve čtyřech situacích: připojení procesu, odpojení procesu, připojení vlákna a odpojení vlákna. Když je knihovna DLL načtena do adresního prostoru procesu, buď při načtení aplikace, která používá, nebo když aplikace požaduje knihovnu DLL za běhu, operační systém vytvoří samostatnou kopii dat knihovny DLL. Tento postup se nazývá *připojení procesu*. K *připojení vlákna* dojde v případě, že proces, který je knihovnou DLL načten, vytvoří nové vlákno. K *odpojení vlákna* dojde při ukončení vlákna a *odpojení procesu* je v případě, že knihovna DLL již není vyžadována a je uvolněna aplikací. Operační systém vytvoří samostatné volání do vstupního bodu knihovny DLL pro každou z těchto událostí a předá argument *důvod* pro každý typ události. Například operační systém odesílá `DLL_PROCESS_ATTACH` jako argument *důvod* k signalizaci připojení procesu.

Knihovna VCRuntime poskytuje funkci vstupního bodu nazvanou `_DllMainCRTStartup` pro zpracování výchozích operací inicializace a ukončení. Při připojení procesu funkce `_DllMainCRTStartup` nastaví kontroly zabezpečení vyrovnávací paměti, inicializuje CRT a další knihovny, inicializuje informace o typu modulu runtime, inicializuje a volá konstruktory pro statická a nemístní data, inicializuje místní úložiště vlákna, zvýší vnitřní statický čítač pro každé připojení a pak zavolá `DllMain`s uživatelem nebo knihovnou. Při odpojení procesu Tato funkce projde kroky v obráceném pořadí. Volá `DllMain`, snižuje vnitřní počítadlo volání destruktorů, volá funkce pro ukončení CRT a registrované `atexit` funkce a oznamuje jakékoli jiné knihovny ukončení. Pokud počítadlo příloh překročí hodnotu nula, funkce vrátí `FALSE`, aby označovala systému Windows, že knihovnu DLL lze uvolnit. Funkce `_DllMainCRTStartup` je také volána během připojení vlákna a odpojení vlákna. V těchto případech kód VCRuntime neprovádí žádnou další inicializaci ani ukončení, a stačí volat `DllMain` k předání zprávy společně. Pokud `DllMain` vrátí `FALSE` z části připojení procesu, selhání signalizace, `_DllMainCRTStartup` volání znovu `DllMain` a předá `DLL_PROCESS_DETACH` jako argument *důvod* , a pak projde zbývající částí procesu ukončení.

Při sestavování knihoven DLL v aplikaci Visual Studio je výchozí vstupní bod `_DllMainCRTStartup` poskytnutý funkcí VCRuntime propojen automaticky. Funkci vstupního bodu pro knihovnu DLL není nutné zadávat pomocí možnosti linkeru [/entry (symbol vstupního bodu)](reference/entry-entry-point-symbol.md) .

> [!NOTE]
> I když je možné zadat jinou funkci vstupního bodu pro knihovnu DLL pomocí možnosti/ENTRY: linker, nedoporučujeme ji, protože vaše funkce vstupního bodu by musela duplikovat vše, co `_DllMainCRTStartup`, ve stejném pořadí. VCRuntime poskytuje funkce, které umožňují duplikovat chování. Můžete například volat [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) hned na procesu připojit, aby podporovala možnost kontroly vyrovnávací paměti [/GS (kontrola zabezpečení vyrovnávací paměti)](reference/gs-buffer-security-check.md) . Můžete zavolat funkci `_CRT_INIT` a předat stejné parametry jako funkci vstupního bodu, aby bylo možné provést zbytek funkcí inicializace nebo ukončení knihovny DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializovat knihovnu DLL

Vaše knihovna DLL může mít inicializační kód, který musí být spuštěn při načtení knihovny DLL. Chcete-li provést vlastní funkce inicializace a ukončení knihovny DLL, `_DllMainCRTStartup` volá funkci nazvanou `DllMain`, kterou lze zadat. `DllMain` musí mít podpis vyžadovaný pro vstupní bod knihovny DLL. Výchozí funkce vstupního bodu `_DllMainCRTStartup` volá `DllMain` pomocí stejných parametrů předaných systémem Windows. Ve výchozím nastavení, pokud neposkytnete funkci `DllMain`, Visual Studio poskytne pro vás jednu za vás a propojí ji tak, aby `_DllMainCRTStartup` vždy měla zavolat. To znamená, že pokud nepotřebujete inicializovat knihovnu DLL, nemusíte při sestavování vaší knihovny DLL provádět žádné zvláštní akce.

Toto je podpis, který se používá pro `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Některé knihovny zabalí funkci `DllMain` za vás. Například v běžné knihovně MFC DLL implementujte `CWinApp` objektů `InitInstance` a `ExitInstance` členské funkce k provedení inicializace a ukončení vyžadované vaší knihovnou DLL. Další podrobnosti naleznete v části [inicializace běžných knihoven MFC DLL](#initializing-regular-dlls) .

> [!WARNING]
> Existují značná omezení, co můžete bezpečně provádět v vstupním bodě knihovny DLL. Podívejte se na [Obecné osvědčené postupy](/windows/win32/Dlls/dynamic-link-library-best-practices) pro konkrétní rozhraní API systému Windows, která nejsou bezpečná pro volání v `DllMain`. Pokud potřebujete cokoli, ale nejjednodušší inicializace, proveďte tuto akci v inicializační funkci pro knihovnu DLL. Můžete požadovat, aby aplikace volaly inicializační funkci po `DllMain` běžel a předtím, než volají jakékoli jiné funkce v knihovně DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializovat běžné knihovny DLL (mimo knihovny MFC)

Chcete-li provést vlastní inicializaci v běžných knihovnách DLL (mimo knihovny MFC), které používají vstupní bod `_DllMainCRTStartup` dodané, váš zdrojový kód knihovny DLL musí obsahovat funkci s názvem `DllMain`. Následující kód prezentuje základní kostru znázorňující, jak by definice `DllMain` mohla vypadat takto:

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
> Starší dokumentace Windows SDK uvádí, že skutečný název funkce vstupního bodu knihovny DLL musí být zadán v příkazovém řádku linkeru s možností/ENTRY. V aplikaci Visual Studio není nutné používat možnost/ENTRY, pokud je název funkce vstupního bodu `DllMain`. Ve skutečnosti platí, že pokud použijete možnost/ENTRY a pojmenujte funkci vstupního bodu na jinou než `DllMain`, CRT se nespustí správně, pokud funkce vstupního bodu neprovede stejná inicializační volání, která `_DllMainCRTStartup` provádí.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicializovat běžné knihovny MFC DLL

Vzhledem k tomu, že běžné knihovny MFC DLL mají objekt `CWinApp`, by měly provádět úlohy inicializace a ukončení ve stejném umístění jako aplikace MFC: ve funkcích `InitInstance` a `ExitInstance` členské funkce třídy odvozené od `CWinApp`knihovny DLL. Protože knihovna MFC poskytuje funkci `DllMain`, která je volána `_DllMainCRTStartup` pro `DLL_PROCESS_ATTACH` a `DLL_PROCESS_DETACH`, neměli byste psát vlastní `DllMain` funkce. Funkce `DllMain` poskytnutá v knihovně MFC volá `InitInstance` při načtení knihovny DLL a volá `ExitInstance` před uvolněním knihovny DLL.

Pravidelná knihovna MFC DLL může sledovat více vláken voláním funkce [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) a [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) ve své funkci `InitInstance`. Tyto funkce umožňují, aby knihovna DLL sledovala data specifická pro vlákno.

V běžné knihovně MFC DLL, která dynamicky odkazuje na knihovnu MFC, pokud používáte libovolnou knihovnu MFC OLE, knihovnu MFC (nebo rozhraní DAO) nebo podporu soketů MFC, v uvedeném pořadí, ladicí knihovny DLL rozšíření MFC MFCO*verze*d. dll, MFCD*verze*d. dll a MFCN*verze*d. dll (kde *verze* je číslo verze) jsou propojeny automaticky. Je nutné zavolat jednu z následujících předdefinovaných inicializačních funkcí pro každou z těchto knihoven DLL, které používáte v běžném `CWinApp::InitInstance`knihovny MFC DLL.

|Typ podpory knihovny MFC|Inicializační funkce, která se má zavolat|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*verze*D. dll)|`AfxOleInitModule`|
|Databáze MFC (MFCD*verze*D. dll)|`AfxDbInitModule`|
|Sokety MFC (MFCN*verze*D. dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicializovat knihovny DLL rozšíření MFC

Knihovny DLL rozšíření MFC nemají objekt odvozený `CWinApp`(stejně jako běžné knihovny MFC DLL), byste měli přidat inicializační a ukončovací kód do funkce `DllMain`, kterou průvodce knihovnou MFC DLL generuje.

Průvodce poskytuje následující kód pro rozšiřující knihovny DLL knihovny MFC. V kódu `PROJNAME` je zástupný symbol pro název vašeho projektu.

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

Vytvoření nového objektu `CDynLinkLibrary` během inicializace umožňuje rozšiřující knihovně MFC DLL pro export `CRuntimeClass` objektů nebo prostředků do klientské aplikace.

Pokud hodláte použít knihovnu DLL rozšíření knihovny MFC z jedné nebo více běžných knihoven MFC DLL, je nutné exportovat inicializační funkci, která vytvoří objekt `CDynLinkLibrary`. Tato funkce musí být volána z každé běžné knihovny MFC DLL, které používají rozšiřující knihovnu MFC DLL. Příslušné místo pro volání této inicializační funkce je ve `InitInstance` členské funkci regulárního objektu `CWinApp`knihovny MFC DLL předtím, než použijete některou z exportovaných tříd nebo funkcí DLL rozšíření MFC.

V `DllMain`, že Průvodce knihovnou MFC DLL generuje, volání `AfxInitExtensionModule` zachytává běhové třídy modulu (`CRuntimeClass` struktury) a také jeho objekty objektů (`COleObjectFactory` objektů), které se použijí při vytvoření objektu `CDynLinkLibrary`. Měli byste ověřit vrácenou hodnotu `AfxInitExtensionModule`; Pokud se z `AfxInitExtensionModule`vrátí nulová hodnota, vrátí se nula z funkce `DllMain`.

Pokud bude vaše knihovna DLL rozšíření knihovny MFC explicitně propojena se spustitelným souborem (což znamená, že se jedná o volání spustitelných souborů `AfxLoadLibrary` pro propojení s knihovnou DLL), měli byste přidat volání `AfxTermExtensionModule` na `DLL_PROCESS_DETACH`. Tato funkce umožňuje knihovně MFC vyčistit rozšiřující knihovnu MFC DLL, když se každý proces odpojí od rozšiřující knihovny MFC DLL (která se stane, když se proces ukončí nebo když je knihovna DLL uvolněna jako výsledek volání `AfxFreeLibrary`). Pokud knihovna DLL rozšíření knihovny MFC bude implicitně propojena s aplikací, volání `AfxTermExtensionModule` není nutné.

Aplikace, které explicitně odkazují na rozšiřující knihovny MFC DLL, musí volat `AfxTermExtensionModule` při uvolnění knihovny DLL. Měly by také používat `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkcí Win32 `LoadLibrary` a `FreeLibrary`), pokud aplikace používá více vláken. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` je zajištěno, že spouštěcí a ukončovací kód, který se spustí, když je načtena knihovna MFC rozšíření DLL, není poškozen globální stav knihovny MFC.

Vzhledem k tomu, že MFCx0. dll je plně inicializován časem `DllMain` je volána, můžete přidělit paměť a volat funkce knihovny MFC v rámci `DllMain` (na rozdíl od 16bitové verze knihovny MFC).

Rozšiřující knihovny DLL se mohou postarat o multithreading tím, že zpracovává `DLL_THREAD_ATTACH` a `DLL_THREAD_DETACH` případy ve funkci `DllMain`. Tyto případy jsou předány do `DllMain`, když se vlákna připojovat a odpojí z knihovny DLL. Volání funkce [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) při připojení ke knihovně DLL umožňuje, aby knihovna DLL udržovala indexy služby Thread Local Storage (TLS) pro každé vlákno připojené ke knihovně DLL.

Všimněte si, že hlavičkový soubor Afxdllx. h obsahuje speciální definice pro struktury používané v knihovnách DLL rozšíření MFC, jako je definice `AFX_EXTENSION_MODULE` a `CDynLinkLibrary`. Tento hlavičkový soubor byste měli zahrnout do rozšiřující knihovny MFC DLL.

> [!NOTE]
>  Je důležité, abyste nedefinovali ani nedefinovali žádná `_AFX_NO_XXX`ová makra v souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší). Tato makra existují pouze k tomu, aby bylo zkontrolováno, zda konkrétní cílová platforma tuto funkci podporuje. Můžete napsat program, aby kontroloval tato makra (například `#ifndef _AFX_NO_OLE_SUPPORT`), ale program by nikdy neměl definovat ani zrušit jejich definování.

Ukázková inicializační funkce, která zpracovává multithreading, je součástí [použití místního úložiště vlákna v dynamické knihovně](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) v Windows SDK. Všimněte si, že ukázka obsahuje funkci vstupního bodu nazvanou `LibMain`, ale tuto funkci byste měli pojmenovat `DllMain` tak, aby fungovala s knihovnami run-time MFC a C.

## <a name="see-also"></a>Viz také

[Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)<br/>
[Vstupní bod DllMain](/windows/win32/Dlls/dllmain)<br/>
[Osvědčené postupy pro dynamickou knihovnu](/windows/win32/Dlls/dynamic-link-library-best-practices)
