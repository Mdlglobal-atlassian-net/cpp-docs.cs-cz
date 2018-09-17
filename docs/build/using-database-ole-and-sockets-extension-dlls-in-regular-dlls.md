---
title: Použití databáze, OLE a Soketových rozšiřujících knihoven DLL v běžných knihovnách MFC DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8fe2c57991ffd15f135fab39c185b6a68f2e9c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701978"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Použití databáze, OLE a Soketových rozšiřujících knihoven DLL v běžných knihovnách MFC DLL

Pokud používáte rozšíření MFC DLL z běžné knihovny MFC DLL MFC – rozšiřující knihovny DLL není zapojenými do **CDynLinkLibrary** objektu řetězce z běžné knihovny MFC DLL, můžete narazit na jeden nebo více sadu souvisejících problémech. Protože podporuje ladicí verze databáze knihovny MFC, OLE a soketů knihovny DLL jsou implementovány jako MFC – rozšiřující knihovny DLL, může se zobrazit funkce podobné problémy, pokud používáte tyto knihovny MFC, i v případě, že nepoužíváte explicitně některý z vlastní MFC – rozšiřující knihovny DLL. Některé příznaky jsou:

- Při pokusu o rekonstrukci objektu typu třídy definované v MFC – rozšiřující knihovny DLL, zpráva "Upozornění: Nelze načíst CYourClass z archivní úrovně. Třída není definována." Zobrazí se v okně ladění trasování a objekt selže při serializaci.

- Může být vyvolána výjimka označující chybný třídy.

- Prostředky uložené v MFC – rozšiřující knihovny DLL se nepodařilo načíst, protože `AfxFindResourceHandle` vrátí **NULL** nebo popisovač nesprávné prostředků.

- `DllGetClassObject`, `DllCanUnloadNow`a `UpdateRegistry`, `Revoke`, `RevokeAll`, a `RegisterAll` členské funkce `COleObjectFactory` nemusí podařit vyhledat objekt pro vytváření tříd definované v MFC – rozšiřující knihovny DLL.

- `AfxDoForAllClasses` nefunguje pro všechny třídy v MFC – rozšiřující knihovny DLL.

- Standardní databáze knihovny MFC, sockets nebo prostředky OLE nepovedlo se načíst. Například **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) vrátí prázdný řetězec, i když se běžné knihovny MFC DLL je správně používá třídy knihovny MFC databáze.

Řešení těchto problémů je pro vytvoření a export inicializační funkce v MFC – rozšiřující knihovny DLL, která vytvoří **CDynLinkLibrary** objektu. Voláním této funkce inicializace právě jedno z každého běžné knihovny MFC DLL, která používá MFC – rozšiřující knihovny DLL.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE, databáze knihovny MFC (nebo rozhraní DAO), nebo podpora soketů knihovny MFC

Pokud používáte žádné MFC OLE, knihovny MFC databáze (nebo rozhraní DAO) nebo soketů knihovny MFC se podporují v uvedeném pořadí v běžné knihovny MFC DLL, ladění MFC MFC – rozšiřující knihovny DLL MFCOxxD.dll, MFCDxxD.dll a MFCNxxD.dll (kde xx je číslo verze) jsou automaticky propojeny. Předdefinované inicializační funkce musí zavolat pro každou z těchto knihoven DLL, které používáte.

Podpora databáze, přidejte volání do `AfxDbInitModule` na vaše běžné knihovny MFC DLL `CWinApp::InitInstance` funkce. Ujistěte se, že k tomuto volání před voláním třídy base ani v žádném přidaném kód, který přistupuje ke knihovně MFCDxxD.dll. Tato funkce nepřijímá žádné parametry a vrací hodnotu void.

Podpora OLE, přidejte volání do `AfxOleInitModule` na vaše běžné knihovny MFC DLL `CWinApp::InitInstance`. Všimněte si, že **COleControlModule InitInstance** volání funkce `AfxOleInitModule` již, takže pokud vytváříte ovládacího prvku OLE a používáte `COleControlModule`, neměli byste přidávat toto volání `AfxOleInitModule`.

Pro podporu sokety, přidejte volání do `AfxNetInitModule` na vaše běžné knihovny MFC DLL `CWinApp::InitInstance`.

Mějte na paměti, že verze sestavení knihovny DLL MFC a aplikací nepoužívejte samostatné knihovny DLL pro databázi, sokety, nebo podporu technologie OLE. Je však bezpečné volat tyto funkce inicializace v režimu vydání.

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary objekty

Během každé operace se už zmínili na začátku tohoto tématu musí vyhledat požadovanou hodnotu nebo objekt knihovny MFC. Během deserializace, například knihovny MFC musí prohledávat všechny aktuálně dostupné třídy za běhu tak, aby odpovídaly objekty v archivní úrovni s jejich správné run-time třída.

Jako součást tato hledání MFC procházením řetěz prohledává všechna rozšíření knihovny DLL MFC používá **CDynLinkLibrary** objekty. **CDynLinkLibrary** objekty automaticky připojí k řetězci během jejich vytváření a jsou vytvářeny každý MFC – rozšiřující knihovny DLL zase během inicializace. Kromě toho všechny moduly (aplikace nebo běžné knihovny MFC DLL) má vlastní řetězec **CDynLinkLibrary** objekty.

Pro rozšiřující knihovny DLL do MFC **CDynLinkLibrary** řetěz, musíte vytvořit **CDynLinkLibrary** objektu v kontextu každého modulu, který používá MFC – rozšiřující knihovny DLL. Proto pokud MFC – rozšiřující knihovny DLL pro použití v běžných knihovnách MFC DLL, musí poskytovat exportované inicializační funkce, která vytvoří **CDynLinkLibrary** objektu. Každý běžné knihovny MFC DLL, která používá MFC – rozšiřující knihovny DLL musí volat exportované inicializační funkce.

Pokud MFC – rozšiřující knihovny DLL je pouze bude používat z aplikace knihovny MFC (.exe) a nikdy z běžné knihovny MFC DLL, pak je dostatečná pro vytvoření **CDynLinkLibrary** objektů v MFC rozšíření knihovny DLL `DllMain`. To je, co dělá rozšíření MFC Průvodce MFC DLL kód knihovny DLL. Při načítání rozšiřující knihovny DLL MFC implicitně `DllMain` načte a spustí před spuštěním aplikace. Žádné **CDynLinkLibrary** vytváření, které jsou zapojeny do výchozího řetězce, že knihovna MFC DLL rezervuje pro aplikaci knihovny MFC.

Všimněte si, že je vhodné mít více **CDynLinkLibrary** objekty z jedné MFC – rozšiřující knihovny DLL v jakémkoliv řetězci, zejména v případě, že bude MFC – rozšiřující knihovny DLL dynamicky uvolněna z paměti. Nevolejte inicializační funkce více než jednou z jakékoli jeden modul.

## <a name="sample-code"></a>Ukázkový kód

Tento vzorový kód předpokládá, že je běžné knihovny MFC DLL implicitně propojení s MFC – rozšiřující knihovny DLL. Toho lze dosáhnout odkazování na knihovnu importu (.lib) MFC – rozšiřující knihovny DLL při sestavování běžné knihovny MFC DLL.

Následující řádky by měl být ve zdroji MFC – rozšiřující knihovny DLL:

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

Je nutné exportovat **InitYourExtDLL** funkce. To dalo udělat pomocí **__declspec(dllexport)** nebo v souboru .def vaše knihovna DLL následujícím způsobem:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Přidejte volání `InitInstance` člen `CWinApp`-odvozenému objektu v každé běžné knihovny MFC DLL MFC – rozšiřující knihovny DLL pomocí:

```
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializace rozšiřující knihovny DLL MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)

- [Inicializovat obvyklé knihovny DLL MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [MFC – rozšiřující knihovny DLL](../build/extension-dlls.md)

- [Běžné knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Viz také

[MFC – rozšiřující knihovny DLL](../build/extension-dlls.md)