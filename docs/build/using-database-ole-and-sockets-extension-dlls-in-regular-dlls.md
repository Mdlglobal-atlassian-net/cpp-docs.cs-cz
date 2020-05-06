---
title: Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314686"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL

Při použití knihovny DLL rozšíření MFC z běžné knihovny MFC DLL, pokud knihovna DLL rozšíření MFC není zapojena do řetězce objektů **CDynLinkLibrary** běžné knihovny MFC DLL, můžete spustit do jedné nebo více sad souvisejících problémů. Vzhledem k tomu, že ladicí verze knihovny MFC, technologie OLE a sokety podporují knihovny DLL, jsou implementovány jako knihovny DLL rozšíření MFC, může se zobrazit podobné problémy, pokud používáte tyto funkce knihovny MFC, a to i v případě, že explicitně nepoužíváte žádnou z vlastních knihoven DLL rozšíření knihovny MFC. Některé příznaky jsou:

- Při pokusu o deserializaci objektu typu třídy definovaného v rozšiřující knihovně MFC DLL se zobrazí zpráva upozornění: nelze načíst CYourClass z archivu. Třída není definována. " zobrazí se v okně ladění trasování a objekt se nedokáže serializovat.

- Výjimka, která značí špatnou třídu, může být vyvolána.

- Prostředky uložené v rozšiřující knihovně MFC DLL se nepodařilo načíst, `AfxFindResourceHandle` protože vrací **hodnotu null** nebo nesprávný popisovač prostředku.

- `DllGetClassObject`, `DllCanUnloadNow`a `UpdateRegistry` `RegisterAll` členské funkce `COleObjectFactory` , `Revoke` `RevokeAll`, a nenaleznou objekt pro vytváření tříd definovaný v rozšiřující knihovně MFC DLL.

- `AfxDoForAllClasses`nefunguje pro žádné třídy v rozšiřující knihovně MFC DLL.

- Nepodařilo se načíst standardní databázi knihovny MFC, sokety nebo prostředky OLE. Například **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) vrátí prázdný řetězec, a to i v případě, že regulární knihovna MFC DLL správně používá třídy databáze knihovny MFC.

Řešení těchto problémů je vytvořit a exportovat inicializační funkci v knihovně DLL rozšíření MFC, která vytvoří objekt **CDynLinkLibrary** . Zavolejte tuto inicializační funkci přesně jednou z každé běžné knihovny MFC DLL, která používá knihovnu DLL rozšíření MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE, MFC Database (nebo DAO) nebo podpora soketů MFC

Pokud používáte jakoukoli knihovnu MFC OLE, knihovnu MFC (nebo rozhraní DAO) nebo podporu soketů MFC v běžné knihovně MFC DLL, v uvedeném pořadí, knihovny MFC DLL rozšíření MFC MFCOxxD. dll, MFCDxxD. dll a MFCNxxD. dll (kde XX je číslo verze) jsou propojeny automaticky. Pro každou z těchto knihoven DLL, které používáte, je nutné zavolat předdefinovanou inicializační funkci.

Pro podporu databáze přidejte volání `AfxDbInitModule` do vaší běžné `CWinApp::InitInstance` funkce knihovny MFC DLL. Zajistěte, aby k tomuto volání došlo před jakýmkoli voláním základní třídy nebo přidaným kódem, který přistupuje k souboru MFCDxxD. dll. Tato funkce nepřijímá žádné parametry a vrací typ void.

Pro podporu technologie OLE přidejte volání `AfxOleInitModule` do vaší regulární knihovny MFC DLL. `CWinApp::InitInstance` Všimněte si, že funkce **COleControlModule InitInstance** již volá `AfxOleInitModule` , takže pokud sestavíte ovládací prvek OLE a používáte `COleControlModule`, neměli byste toto volání přidat do `AfxOleInitModule`.

Pro podporu soketů přidejte volání `AfxNetInitModule` do vaší běžné knihovny MFC DLL. `CWinApp::InitInstance`

Sestavení vydaných verzí knihoven MFC DLL a aplikací nepoužívají samostatné knihovny DLL pro databáze, sokety nebo podporu technologie OLE. Je však bezpečné volat tyto inicializační funkce v režimu vydání.

## <a name="cdynlinklibrary-objects"></a>Objekty CDynLinkLibrary

V každé z operací uvedených na začátku tohoto tématu potřebuje MFC vyhledat požadovanou hodnotu nebo objekt. Například při deserializaci potřebuje MFC vyhledat všechny aktuálně dostupné třídy run-time, aby odpovídaly objektům v archivu, které mají správnou běhovou třídu.

V rámci těchto hledání knihovna MFC prohledává všechny používané rozšiřující knihovny MFC pomocí procházení řetězce objektů **CDynLinkLibrary** . Objekty **CDynLinkLibrary** se automaticky připojí k řetězci během jejich konstrukce a jsou vytvářeny každou rozšiřující knihovnou DLL knihovny MFC během inicializace. Kromě toho má každý modul (aplikace nebo běžná knihovna MFC DLL) vlastní řetězec objektů **CDynLinkLibrary** .

Pro rozšiřující knihovnu DLL knihovny MFC, která je zapojena do řetězce **CDynLinkLibrary** , musí vytvořit objekt **CDynLinkLibrary** v kontextu každého modulu, který používá knihovnu DLL rozšíření MFC. Proto pokud se knihovna DLL rozšíření MFC bude používat z běžných knihoven DLL knihovny MFC, musí poskytnout exportovanou inicializační funkci, která vytvoří objekt **CDynLinkLibrary** . Každá běžná knihovna MFC DLL, která používá knihovnu DLL rozšíření MFC, musí volat exportovanou inicializační funkci.

Pokud se knihovna DLL rozšíření MFC bude používat jenom z aplikace MFC (. exe) a nikdy z běžné knihovny DLL knihovny MFC, stačí vytvořit objekt **CDynLinkLibrary** v knihovně DLL rozšíření MFC `DllMain`. To je to, co provede Průvodce knihovnou MFC DLL MFC kódu DLL. Při implicitním načítání knihovny DLL rozšíření knihovny MFC `DllMain` se načte a spustí před tím, než se aplikace spustí. Jakékoli vytváření programu **CDynLinkLibrary** jsou kabelové do výchozího řetězce, který knihovna MFC DLL rezervuje pro aplikaci MFC.

Všimněte si, že se jedná o neplatnou představu o více objektech **CDynLinkLibrary** z jedné knihovny DLL rozšíření MFC v jakémkoli řetězci, zejména pokud se rozšiřující knihovna MFC dynamicky uvolní z paměti. Nevolejte inicializační funkci více než jednou z jednoho modulu.

## <a name="sample-code"></a>Příklad kódu

Tento vzorový kód předpokládá, že běžná knihovna MFC DLL je implicitně propojena s knihovnou DLL rozšíření MFC. K tomu je potřeba při vytváření běžné knihovny MFC DLL propojit knihovnu importu (. lib) rozšiřující knihovny MFC DLL.

Následující řádky by měly být ve zdroji rozšiřující knihovny MFC DLL:

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

Nezapomeňte exportovat funkci **InitYourExtDLL** . To lze provést pomocí **__declspec (dllexport)** nebo v souboru. def knihovny DLL následujícím způsobem:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Přidejte volání `InitInstance` členu `CWinApp`odvozeného objektu v každé běžné knihovně MFC DLL pomocí knihovny DLL rozšíření MFC:

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

- [Inicializace knihovny DLL rozšíření MFC](run-time-library-behavior.md#initializing-extension-dlls)

- [Inicializovat běžné knihovny MFC DLL](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [MFC – rozšiřující knihovny DLL](extension-dlls.md)

- [Běžné knihovny MFC DLL staticky propojené do MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Použití knihovny MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Viz také

[MFC – rozšiřující knihovny DLL](extension-dlls.md)
