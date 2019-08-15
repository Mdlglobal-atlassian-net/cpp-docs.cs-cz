---
title: Knihovny DLL a C++ chování běhové knihovny jazyka Visual runtime
ms.date: 05/06/2019
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
ms.openlocfilehash: d44f3bf7a8b06f567b1af221e17085d589e56aca
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492609"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Knihovny DLL a C++ chování běhové knihovny jazyka Visual runtime

Když vytváříte dynamickou knihovnu (DLL) pomocí sady Visual Studio, ve výchozím nastavení linker zahrnuje Visual C++ Run-Time Library (VCRuntime). VCRuntime obsahuje kód potřebný k inicializaci a ukončení spustitelného souboru CC++ /. Při propojení s knihovnou DLL kód VCRuntime poskytuje interní funkci vstupního bodu knihovny DLL s názvem `_DllMainCRTStartup` , která zpracovává zprávy operačního systému Windows do knihovny DLL pro připojení nebo odpojení od procesu nebo vlákna. `_DllMainCRTStartup` Funkce provádí základní úlohy, jako je nastavení zabezpečení vyrovnávací paměti zásobníku, inicializace a ukončení knihovny run-time Library (CRT) a volání konstruktorů a destruktorů pro statické a globální objekty. `_DllMainCRTStartup`volá také funkce připojení pro jiné knihovny, jako je WinRT, MFC a ATL, aby bylo možné provést svou vlastní inicializaci a ukončení. Bez této inicializace by CRT a jiné knihovny, stejně jako statické proměnné, byly ponechány v neinicializovaném stavu. Stejné VCRuntime interní inicializace a rutiny ukončení jsou volány, pokud vaše knihovna DLL používá staticky propojenou CRT nebo dynamicky propojenou knihovnu CRT DLL.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Výchozí vstupní bod knihovny DLL – _DllMainCRTStartup

V systému Windows všechny knihovny DLL mohou obsahovat volitelnou funkci vstupního bodu, která je `DllMain`obvykle volána, která je volána pro inicializaci i ukončení. Získáte tak možnost přidělit nebo uvolnit další prostředky podle potřeby. Systém Windows volá funkci vstupního bodu ve čtyřech situacích: připojení procesu, odpojení procesu, připojení vlákna a odpojení vlákna. Když je knihovna DLL načtena do adresního prostoru procesu, buď při načtení aplikace, která používá, nebo když aplikace požaduje knihovnu DLL za běhu, operační systém vytvoří samostatnou kopii dat knihovny DLL. Tento postup se nazývá *připojení procesu*. K *připojení vlákna* dojde v případě, že proces, který je knihovnou DLL načten, vytvoří nové vlákno. K *odpojení vlákna* dojde při ukončení vlákna a *odpojení procesu* je v případě, že knihovna DLL již není vyžadována a je uvolněna aplikací. Operační systém vytvoří samostatné volání do vstupního bodu knihovny DLL pro každou z těchto událostí a předá argument *důvod* pro každý typ události. Například operační systém odesílá `DLL_PROCESS_ATTACH` jako argument *důvod* k signalizaci připojení procesu.

Knihovna VCRuntime poskytuje funkci vstupního bodu volanou `_DllMainCRTStartup` pro zpracování výchozích operací inicializace a ukončení. Při připojení `_DllMainCRTStartup` procesu nastaví funkce kontrolu zabezpečení vyrovnávací paměti, inicializuje CRT a další knihovny, inicializuje informace o typu modulu runtime, inicializuje a volá konstruktory pro statická a nemístní data, inicializuje místní úložiště vlákna. , navýší interní statický čítač pro každé připojení a pak zavolá uživatelem nebo knihovnu zadanou `DllMain`v knihovně. Při odpojení procesu Tato funkce projde kroky v obráceném pořadí. Volá `DllMain`, snižuje vnitřní počítadlo volání destruktorů, volá funkce pro ukončení a registrované `atexit` funkce CRT a oznamuje jakékoli jiné knihovny ukončení. Pokud počítadlo příloh překročí nulu, vrátí `FALSE` funkce, aby označovala systému Windows, že knihovnu DLL lze uvolnit. `_DllMainCRTStartup` Funkce je také volána během připojení vlákna a odpojení vlákna. V těchto případech kód VCRuntime neprovádí žádnou další inicializaci ani ukončení, a stačí volat `DllMain` , aby se zpráva předala společně. Pokud `DllMain` se `FALSE` vrátí z příkazového připojení procesu, selhání `_DllMainCRTStartup` signalizace `DLL_PROCESS_DETACH` , volání `DllMain` znovu a předají se jako argument *důvod* , a pak projde zbytek procesu ukončení.

Při sestavování knihoven DLL v aplikaci Visual Studio je `_DllMainCRTStartup` výchozí vstupní bod dodaný funkcí VCRuntime propojen automaticky. Funkci vstupního bodu pro knihovnu DLL není nutné zadávat pomocí možnosti linkeru [/entry (symbol vstupního bodu)](reference/entry-entry-point-symbol.md) .

> [!NOTE]
> Přestože je možné zadat jinou funkci vstupního bodu pro knihovnu DLL pomocí možnosti/Entry: linker, nedoporučujeme ji, protože vaše funkce vstupního bodu by musela duplikovat vše `_DllMainCRTStartup` , co dělá, ve stejném pořadí. VCRuntime poskytuje funkce, které umožňují duplikovat chování. Například můžete volat [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) okamžitě při připojení procesu k podpoře možnosti kontroly vyrovnávací paměti [/GS (kontrola zabezpečení vyrovnávací paměti)](reference/gs-buffer-security-check.md) . `_CRT_INIT` Funkci lze volat a předat stejné parametry jako funkci vstupního bodu, aby bylo možné provést zbytek funkcí inicializace nebo ukončení knihovny DLL.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Inicializovat knihovnu DLL

Vaše knihovna DLL může mít inicializační kód, který musí být spuštěn při načtení knihovny DLL. Chcete-li provést vlastní funkce inicializace a ukončení knihovny DLL, `_DllMainCRTStartup` zavolá funkci nazvanou `DllMain` , která může být k dispozici. `DllMain` Je nutné, aby byl podpis vyžadován pro vstupní bod knihovny DLL. Výchozí volání `_DllMainCRTStartup` `DllMain` funkce vstupního bodu používá stejné parametry předané systémem Windows. Ve výchozím nastavení, pokud neposkytnete `DllMain` funkci, Visual Studio vám nabídne jednu za vás a propojí ji tak, `_DllMainCRTStartup` aby vždy vyvolala. To znamená, že pokud nepotřebujete inicializovat knihovnu DLL, nemusíte při sestavování vaší knihovny DLL provádět žádné zvláštní akce.

Tento podpis se používá pro `DllMain`:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Některé knihovny zabalí `DllMain` funkci za vás. Například v běžné knihovně MFC DLL implementujte `CWinApp` `InitInstance` objekt a `ExitInstance` členské funkce pro provedení inicializace a ukončení vyžadované vaší knihovnou DLL. Další podrobnosti naleznete v části [inicializace běžných knihoven MFC DLL](#initializing-regular-dlls) .

> [!WARNING]
> Existují značná omezení, co můžete bezpečně provádět v vstupním bodě knihovny DLL. Další informace najdete v `DllMain`tématu [Obecné osvědčené postupy](/windows/win32/Dlls/dynamic-link-library-best-practices) pro konkrétní rozhraní API systému Windows, která nejsou bezpečná pro volání. Pokud potřebujete cokoli, ale nejjednodušší inicializace, proveďte tuto akci v inicializační funkci pro knihovnu DLL. Můžete požadovat, aby aplikace volaly inicializační funkci po `DllMain` spuštění a předtím, než volají jakékoli jiné funkce v knihovně DLL.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Inicializovat běžné knihovny DLL (mimo knihovny MFC)

Chcete-li provést vlastní inicializaci v běžných knihovnách DLL (mimo knihovny MFC), které používají `_DllMainCRTStartup` vstupní bod dodaný VCRuntime, váš zdrojový kód knihovny DLL musí `DllMain`obsahovat funkci s názvem. Následující kód prezentuje základní kostru, která ukazuje, jak `DllMain` definice může vypadat takto:

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
> Starší dokumentace Windows SDK uvádí, že skutečný název funkce vstupního bodu knihovny DLL musí být zadán v příkazovém řádku linkeru s možností/ENTRY. V aplikaci Visual Studio není nutné používat možnost/ENTRY, pokud je `DllMain`název funkce vstupního bodu. Ve skutečnosti platí, že pokud použijete možnost/ENTRY a pojmenujte funkci vstupního bodu na jinou `DllMain`než, CRT se neinicializuje správně, pokud funkce vstupního bodu neprovede stejné inicializační volání, které `_DllMainCRTStartup` provádí.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Inicializovat běžné knihovny MFC DLL

Vzhledem k tomu, že běžné `CWinApp` knihovny MFC DLL mají objekt, by měly provádět úlohy inicializace a ukončení ve stejném umístění jako aplikace knihovny MFC: `InitInstance` v `ExitInstance` členských funkcích a funkce odvozené knihovny `CWinApp`dll. Deník. Protože knihovna MFC poskytuje `DllMain` funkci, která je `_DllMainCRTStartup` volána pro `DLL_PROCESS_ATTACH` a `DLL_PROCESS_DETACH`, neměli byste psát vlastní `DllMain` funkci. Funkce poskytovaná `DllMain` knihovnou MFC `InitInstance` volá při načtení knihovny DLL a volá `ExitInstance` před uvolněním knihovny DLL.

Pravidelná knihovna MFC DLL může sledovat více vláken voláním funkce [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) a [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) ve své `InitInstance` funkci. Tyto funkce umožňují, aby knihovna DLL sledovala data specifická pro vlákno.

V běžné knihovně MFC DLL, která dynamicky odkazuje na knihovnu MFC, pokud používáte jakoukoli knihovnu MFC OLE, knihovnu MFC (nebo rozhraní DAO) nebo podporu soketů MFC, v uvedeném pořadí, knihovny DLL rozšíření ladění knihovny MFC MFCO*verze*d. dll, MFCD*verze*d. dll a MFCN*verze*d. dll ( kde *verze* je číslo verze), se automaticky propojí. Je nutné zavolat jednu z následujících předdefinovaných inicializačních funkcí pro každou z těchto knihoven DLL, které používáte v běžné knihovně MFC DLL `CWinApp::InitInstance`.

|Typ podpory knihovny MFC|Inicializační funkce, která se má zavolat|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*verze*D. dll)|`AfxOleInitModule`|
|Databáze MFC (MFCD*verze*D. dll)|`AfxDbInitModule`|
|Sokety MFC (MFCN*verze*D. dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Inicializovat knihovny DLL rozšíření MFC

Vzhledem k tomu, že knihovny DLL `CWinApp`rozšíření MFC nemají objekt odvozený (stejně jako běžné knihovny MFC DLL), měli byste přidat inicializační a ukončovací kód `DllMain` do funkce, kterou generuje Průvodce knihovnou MFC DLL.

Průvodce poskytuje následující kód pro rozšiřující knihovny DLL knihovny MFC. V kódu `PROJNAME` je zástupný symbol pro název vašeho projektu.

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

Vytvoření nového `CDynLinkLibrary` objektu během inicializace umožňuje rozšiřující knihovně DLL knihovny MFC exportovat `CRuntimeClass` objekty nebo prostředky do klientské aplikace.

Pokud hodláte použít knihovnu DLL rozšíření MFC z jedné nebo více běžných knihoven DLL knihovny MFC, je nutné exportovat inicializační funkci, která vytvoří `CDynLinkLibrary` objekt. Tato funkce musí být volána z každé běžné knihovny MFC DLL, které používají rozšiřující knihovnu MFC DLL. Příslušné místo pro volání této inicializační funkce je v `InitInstance` členské funkci normálního objektu odvozené knihovny MFC `CWinApp`DLL předtím, než použijete některé z exportovaných tříd nebo funkcí DLL rozšiřující knihovny MFC.

`CDynLinkLibrary` `COleObjectFactory` `CRuntimeClass` `AfxInitExtensionModule` V případě ,žePrůvodceknihovnyMFCDLLgeneruje,volánízachytíběhovétřídy(struktury)moduluruntimeatakéjehoobjektyobjektupropoužitípřivytvořeníobjektu.`DllMain` Měli byste ověřit vrácenou hodnotu `AfxInitExtensionModule`. Pokud je vrácena nulová hodnota z `AfxInitExtensionModule`, vrátí nula z vaší `DllMain` funkce.

Pokud bude vaše knihovna DLL rozšíření knihovny MFC explicitně propojena se spustitelným souborem (což `AfxLoadLibrary` znamená, že se jedná o spustitelná volání pro propojení s knihovnou `DLL_PROCESS_DETACH`dll), měli byste přidat `AfxTermExtensionModule` volání na. Tato funkce umožňuje, aby knihovna MFC vyčistila rozšiřující knihovnu MFC DLL, když se každý proces odpojí od rozšiřující knihovny MFC DLL (která se stane, když se proces ukončí nebo když je knihovna DLL uvolněna `AfxFreeLibrary` jako výsledek volání). Pokud knihovna DLL rozšíření knihovny MFC bude implicitně propojena s aplikací, volání `AfxTermExtensionModule` není nutné.

Aplikace, které explicitně odkazují na rozšiřující knihovny MFC DLL `AfxTermExtensionModule` , musí volat při uvolnění knihovny DLL. Měly by také používat `AfxLoadLibrary` a `AfxFreeLibrary` (namísto funkcí `LoadLibrary` Win32 a `FreeLibrary`), pokud aplikace používá více vláken. Pomocí `AfxLoadLibrary` a`AfxFreeLibrary` zajistí, že kód spuštění a vypnutí, který se spustí, když je načtena knihovna DLL MFC a uvolněna, není poškozen globální stav knihovny MFC.

Vzhledem k tomu, že MFCx0. dll je plně inicializován `DllMain` časem je volána, můžete přidělit paměť a volat funkce knihovny MFC `DllMain` v rámci (na rozdíl od 16bitové verze knihovny MFC).

Rozšiřující knihovny DLL se mohou postarat o multithreading tím, že `DLL_THREAD_ATTACH` zpracovává `DLL_THREAD_DETACH` případy a ve `DllMain` funkci. Tyto případy jsou předány `DllMain` do okamžiku, kdy vlákna připojí a odpojí z knihovny DLL. Volání funkce [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) při připojení ke knihovně DLL umožňuje, aby knihovna DLL udržovala indexy služby Thread Local Storage (TLS) pro každé vlákno připojené ke knihovně DLL.

Všimněte si, že hlavičkový soubor Afxdllx. h obsahuje speciální definice pro struktury používané v knihovnách DLL rozšíření MFC, jako `AFX_EXTENSION_MODULE` je `CDynLinkLibrary`definice pro a. Tento hlavičkový soubor byste měli zahrnout do rozšiřující knihovny MFC DLL.

> [!NOTE]
>  Je důležité, abyste nedefinovali ani nedefinovali žádná `_AFX_NO_XXX` makra v Stdafx. h. Tato makra existují pouze k tomu, aby bylo zkontrolováno, zda konkrétní cílová platforma tuto funkci podporuje. Můžete napsat program pro kontrolu těchto maker (například `#ifndef _AFX_NO_OLE_SUPPORT`), ale program by nikdy neměl definovat ani zrušit jejich definici.

Ukázková inicializační funkce, která zpracovává multithreading, je součástí [použití místního úložiště vlákna v dynamické knihovně](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) v Windows SDK. Všimněte si, že ukázka obsahuje funkci vstupního bodu s názvem `LibMain`, ale tuto funkci `DllMain` byste měli pojmenovat tak, aby fungovala s knihovnami runtime MFC a C.

## <a name="see-also"></a>Viz také:

[Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)<br/>
[Vstupní bod DllMain](/windows/win32/Dlls/dllmain)<br/>
[Osvědčené postupy pro dynamickou knihovnu](/windows/win32/Dlls/dynamic-link-library-best-practices)
