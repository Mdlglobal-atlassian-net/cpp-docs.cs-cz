---
title: Pomocí databáze OLE a Sockets MFC rozšiřující knihovny DLL v běžných knihovnách DLL MFC | Microsoft Docs
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
ms.openlocfilehash: f902f3b512b5684cf185829fdf4346b8851ff8ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391402"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Pomocí databáze OLE a Sockets MFC rozšiřující knihovny DLL v běžných knihovnách DLL knihovny MFC
Při použití knihovnu DLL z běžné knihovny MFC DLL, pokud MFC – rozšiřující knihovny DLL není připojená do **CDynLinkLibrary** objektu řetězu regulární knihovny MFC DLL, můžete narazit na jeden nebo více sady souvisejících problémech. Protože verze pro ladění MFC databáze, technologie OLE a Sockets podporují knihovny DLL jsou implementované jako MFC – rozšiřující knihovny DLL, může se zobrazit podobné problémy, pokud používáte tyto MFC funkce, i v případě, že nepoužíváte explicitně všechny vlastní MFC – rozšiřující knihovny DLL. Některé příznaky jsou:  
  
-   Při pokusu o deserializaci objektu typu třídy definované v rozšíření MFC DLL, zpráva "Upozornění: Nelze načíst CYourClass z archivu. Třída není definována." Zobrazí se v okně trasování ladění a objekt selže k serializaci.  
  
-   Může být vyvolána výjimka označující chybnou třídu.  
  
-   Prostředky, které jsou uložené v rozšíření MFC DLL nepodaří načíst, protože `AfxFindResourceHandle` vrátí **NULL** nebo popisovač nesprávný prostředků.  
  
-   `DllGetClassObject`, `DllCanUnloadNow`a `UpdateRegistry`, `Revoke`, `RevokeAll`, a `RegisterAll` členské funkce `COleObjectFactory` nepodaří najít objekt třídy definované v rozšíření MFC DLL.  
  
-   `AfxDoForAllClasses` pro všechny třídy v rozšíření MFC DLL nefunguje.  
  
-   Standardní MFC databáze, sokety nebo prostředky OLE nepodaří načíst. Například **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) vrátí prázdný řetězec, i když běžné knihovny MFC DLL správně používá třídy MFC databáze.  
  
 Řešení těchto problémů, které se má vytvořit a exportovat inicializační funkce v rozšíření MFC DLL, která vytvoří **CDynLinkLibrary** objektu. Volání této funkce inicializace přesně po z každé běžné knihovny MFC DLL, která používá rozšíření MFC DLL.  
  
## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE, MFC databáze (nebo DAO), nebo podpora soketů knihovny MFC  
 Pokud používáte žádné MFC OLE, MFC databáze (nebo DAO) nebo MFC sokety v pravidelných MFC DLL v uvedeném pořadí, MFC ladění MFC – rozšiřující knihovny DLL MFCOxxD.dll, MFCDxxD.dll a MFCNxxD.dll (kde xx je číslo verze) jsou propojeny automaticky. Inicializace předdefinované funkce musí volat pro každou z těchto knihoven DLL, které používáte.  
  
 Podpora databáze, přidejte volání `AfxDbInitModule` na vaše regulární MFC DLL `CWinApp::InitInstance` funkce. Zajistěte, aby toto volání dojde před voláním jakékoli základní třídy nebo přidané kód, který přistupuje ke knihovně MFCDxxD.dll. Tato funkce nepřijímá žádné parametry a vrátí prázdnou hodnotu.  
  
 Podpora OLE, že přidáte volání `AfxOleInitModule` na vaše regulární MFC DLL `CWinApp::InitInstance`. Všimněte si, že **COleControlModule InitInstance** volání funkce `AfxOleInitModule` již, takže pokud vytváříte ovládacího prvku OLE a používáte `COleControlModule`, doporučujeme nepřidávat toto volání `AfxOleInitModule`.  
  
 Pro podporu Sockets přidejte volání `AfxNetInitModule` na vaše regulární MFC DLL `CWinApp::InitInstance`.  
  
 Poznámka: verze sestavení MFC – knihovny DLL a aplikace nepoužívejte samostatné knihovny DLL pro databázi, sokety nebo podporu OLE. Je však bezpečné volat tyto funkce inicializace v režimu vydání.  
  
## <a name="cdynlinklibrary-objects"></a>Objekty CDynLinkLibrary  
 Během každé operace a na začátku tohoto tématu musí MFC vyhledejte požadovanou hodnotu nebo objekt. Během deserializace, například MFC musí prohledávat všechny aktuálně k dispozici třídy běhu tak, aby odpovídaly objekty v archivu s jejich správné run-time třída.  
  
 Jako součást tato hledání, MFC projde přes všechny DLL rozšíření MFC používá při prohledávání řetězce z **CDynLinkLibrary** objekty. **CDynLinkLibrary** objekty automaticky připojí k řetězci během jejich vytváření a jsou vytvářeny každý MFC – rozšiřující knihovny DLL zase během inicializace. Kromě toho má každý modul (aplikace nebo běžné knihovny MFC DLL) vlastní řetězec **CDynLinkLibrary** objekty.  
  
 Pro rozšíření MFC DLL do **CDynLinkLibrary** řetězci, musíte vytvořit **CDynLinkLibrary** objektu v kontextu každý modul, který používá rozšíření MFC DLL. Proto pokud rozšíření MFC DLL pro použití v pravidelných MFC – knihovny DLL, je nutné zadat exportovaný inicializační funkci, která vytvoří **CDynLinkLibrary** objektu. Každých regulární MFC DLL, která používá rozšíření MFC DLL musí volat funkci exportovaný inicializace.  
  
 Pokud rozšíření MFC DLL bude jenom použít z aplikace MFC (.exe) a nikdy běžné knihovny MFC DLL, pak je dostačující k vytvoření **CDynLinkLibrary** objekt v MFC rozšíření knihovny DLL `DllMain`. Toto je, jaké jsou rozšíření MFC DLL Průvodce MFC DLL kódu. Při načítání knihovnu DLL implicitně `DllMain` načte a spustí před spuštěním aplikace. Všechny **CDynLinkLibrary** vytvoření zapojeny do výchozího řetězce, MFC DLL rezervuje pro aplikace MFC.  
  
 Všimněte si, že je vhodné více **CDynLinkLibrary** objekty z jedné MFC – rozšiřující knihovny DLL v jakémkoliv řetězci, hlavně pokud rozšíření MFC DLL dynamicky uvolněna z paměti. Nevolejte funkce inicializace více než jednou z jakéhokoliv modulu.  
  
## <a name="sample-code"></a>Ukázkový kód  
 Tento ukázkový kód předpokládá, že je běžné knihovny MFC DLL implicitně propojení s příponou MFC DLL. Toho dosahuje pomocí propojení do knihovny importu (LIB) rozšíření MFC DLL při sestavování běžné knihovny MFC DLL.  
  
 Ve zdroji MFC – rozšiřující knihovny DLL musí být následující řádky:  
  
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
  
 Je nutné exportovat **InitYourExtDLL** funkce. To lze provést pomocí **__declspec(dllexport)** nebo v souboru .def knihovny DLL následujícím způsobem:  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 Přidejte volání `InitInstance` členem `CWinApp`-odvozené objekt v každé regulární MFC DLL pomocí rozšíření MFC DLL:  
  
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
  
-   [Inicializovat knihovnu DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
-   [Inicializovat běžné knihovny MFC DLL](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [MFC – rozšiřující knihovny DLL](../build/extension-dlls.md)  
  
-   [Běžné knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Běžné knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC – rozšiřující knihovny DLL](../build/extension-dlls.md)