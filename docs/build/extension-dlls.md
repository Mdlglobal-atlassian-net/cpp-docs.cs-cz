---
title: Rozšiřující knihovny DLL
ms.date: 05/06/2019
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220774"
---
# <a name="mfc-extension-dlls"></a>MFC – rozšiřující knihovny DLL

MFC – rozšiřující knihovny DLL je knihovnu DLL, která se obvykle implementují opakovaně použitelné třídy odvozené z existujících tříd knihovny Microsoft Foundation Class.

Rozšiřující knihovny DLL MFC má následující funkce a požadavky:

- Klientský spustitelný soubor musí být zkompilovaná aplikace knihovny MFC `_AFXDLL` definované.

- Rozšiřující knihovny DLL MFC je také možné pomocí běžné knihovny MFC DLL staticky propojené do MFC.

- MFC – rozšiřující knihovny DLL, by měl být zkompilován s `_AFXEXT` definované. To přinutí `_AFXDLL` také definovat a zajistí, že správné deklarace se použije souborech hlaviček knihovny MFC. Také zajistí, že `AFX_EXT_CLASS` je definován jako `__declspec(dllexport)` při sestavování knihovny DLL, která je nutná, pokud použijete toto makro k deklarování tříd ve vaší MFC – rozšiřující knihovny DLL.

- MFC – rozšiřující knihovny DLL by neměl vytvořit instanci třídy odvozené od `CWinApp`, ale by se neměla spoléhat na klientské aplikace (nebo DLL), k poskytnutí tohoto objektu.

- MFC – rozšiřující knihovny DLL by měly, ale poskytnout `DllMain` fungovat a proveďte všechny nezbytné inicializace.

Rozšiřující knihovny DLL se vytvářejí pomocí knihovny DLL verze knihovny MFC (označované také jako sdílených verzí knihovny MFC). Pouze spustitelné soubory knihovny MFC (aplikace nebo běžných knihovnách MFC DLL), které jsou integrovány s sdílených verzí knihovny MFC můžete použít rozšiřující knihovny DLL MFC. Klientská aplikace i MFC – rozšiřující knihovny DLL musí používat stejnou verzi knihovny MFCx0.dll. S rozšiřující knihovny DLL MFC lze odvozovat nové vlastní třídy knihovny MFC a potom nabídnout tato rozšířená verze knihovny MFC k aplikacím, které volají vaši knihovnu DLL.

Rozšiřující knihovny DLL lze použít také pro předávání mezi aplikací a knihovny DLL MFC odvozené objekty. Členské funkce související s předaným objektem existovat v modulu, ve kterém byl objekt vytvořen. Protože tyto funkce se správně vyexportovala při použití sdílené knihovny DLL verze knihovny MFC, můžete předat volně knihovny MFC nebo knihovny MFC odvozenému objektu ukazatele mezi aplikací a MFC – rozšiřující knihovny DLL načte.

Rozšiřující knihovny DLL MFC používá stejným způsobem jako aplikace používá sdílenou knihovnu DLL verze knihovny MFC, s několika další důležité informace o sdílených verzí knihovny MFC:

- Nemá `CWinApp`-odvozenému objektu. Musí pracovat `CWinApp`-odvozenému objektu klientské aplikace. To znamená, že klientská aplikace vlastní hlavní pumpu zpráv, nečinné smyčky a tak dále.

- Volá `AfxInitExtensionModule` v jeho `DllMain` funkce. Návratová hodnota této funkce by měly být porovnány. Pokud není vrácena nulová hodnota z `AfxInitExtensionModule`, vrátí 0 z vašich `DllMain` funkce.

- Vytvoří **CDynLinkLibrary** během inicializace objektu, pokud MFC – rozšiřující knihovny DLL chce exportovat `CRuntimeClass` objekty nebo prostředky do aplikace.

Dříve než ve verzi 4.0 knihovna MFC DLL tento typ byla volána AFXDLL. AFXDLL – odkazuje `_AFXDLL` symbol preprocesoru, který je definován při vytváření knihovny DLL.

Importovat knihovny pro sdílenou verzi knihovny MFC jsou pojmenovány podle konvence je popsáno v [zásady vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual Studio poskytuje předem připravených verze knihovny MFC DLL plus číslo z non - MFC knihovny DLL, kterou můžete použít a distribuovat s vašimi aplikacemi. Tyto jsou zdokumentované v souboru Redist.txt, který je nainstalován do složky, Program Files\Microsoft Visual Studio.

Pokud exportujete pomocí souboru .def, umístěte následující kód na začátek a konec hlavičkový soubor:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Tyto čtyři řádky zajistí, že je váš kód správně kompilován pro rozšiřující knihovny DLL MFC. Vynechání těchto čtyř řádků může způsobit, že vaše DLL knihovna bude kompilovat nebo nesprávně propojení.

Pokud je potřeba předat knihovny MFC nebo ukazatel objektu odvozené knihovny MFC z knihovny DLL MFC, knihovny DLL nebo by měla být rozšiřující knihovny DLL MFC. Členské funkce související s předaným objektem existovat v modulu, ve kterém byl objekt vytvořen. Protože tyto funkce se správně vyexportovala při použití sdílené knihovny DLL verze knihovny MFC, můžete předat volně knihovny MFC nebo knihovny MFC odvozenému objektu ukazatele mezi aplikací a MFC – rozšiřující knihovny DLL načte.

Z důvodu název pozměnění a export problémy s C++ exportovat seznam z MFC – rozšiřující knihovny DLL může lišit mezi ladění a maloobchodní verze stejné knihovny DLL a knihovny DLL pro různé platformy. Verze knihovny MFCx0.dll má přibližně 2 000 exportovaných vstupní bod; ladicí verze knihovny MFCx0D.dll má přibližně 3000 exportoval se vstupní body.

## <a name="memory-management"></a>Správa paměti

MFCx0.dll a všechny MFC – rozšiřující knihovny DLL načten do klientské aplikace adresní prostor používat stejné přidělení paměti, načítání prostředků a jiné globální stavy MFC jako kdyby byly ve stejné aplikaci. To je důležité, protože knihovny MFC DLL a běžných knihovnách MFC DLL přesným opakem a každou knihovnu DLL přidělování mimo svůj vlastní fond paměti k dispozici.

Pokud rozšiřující knihovny DLL MFC přidělí paměť, že paměť můžete libovolně kombinovat s jakýkoli jiný objekt přidělený aplikace. Také pokud se nepodaří aplikaci, která dynamicky propojuje ke knihovně MFC, ochranu operačního systému udržuje integrity jakékoli jiné aplikace knihovny MFC, knihovny DLL pro sdílení obsahu.

Podobně jako jiné globální stavy knihovny MFC, jako je aktuální spustitelný soubor a načíst prostředky z, jsou také sdílené mezi klientskou aplikaci a všechny rozšiřující knihovny DLL MFC i MFCx0.dll.

## <a name="sharing-resources-and-classes"></a>Sdílení prostředků a třídy

Export prostředků se provádí prostřednictvím seznamu prostředků. Každá aplikace obsahuje jednotlivě propojený seznam **CDynLinkLibrary** objekty. Při hledání pro určitý prostředek, podívejte se nejprve sledovat aktuální modul prostředků většinu standardní implementace MFC, který se načítá prostředky (`AfxGetResourceHandle`) a pokud prostředek nenajde procházení seznamu **CDynLinkLibrary** objekty došlo k pokusu o načtení požadovaný prostředek.

Procházení seznamu má nevýhody, že je o něco pomalejší a vyžaduje správu rozsahů ID prostředků. To má výhodu, že klientská aplikace, která obsahuje odkazy na několik rozšiřující knihovny DLL MFC můžete použít libovolný zadaná knihovna DLL prostředků bez nutnosti zadávat popisovač instance knihovny DLL. `AfxFindResourceHandle` rozhraní API slouží k procházení seznamu prostředků pro hledání shody daného. Přijímá název a typ prostředku a vrátí popisovač prostředku, ve kterém byl nalezen první (nebo hodnota NULL).

Pokud vás seznamu a jenom načítat prostředky z určité místo, kde nechcete, pomocí funkce `AfxGetResourceHandle` a `AfxSetResourceHandle` uložit původní popisovač a nastavit nový popisovač. Je potřeba obnovit původní popisovač prostředku, pak se vraťte do klientské aplikace. Příklad použití tohoto přístupu pro explicitní načtení nabídky, naleznete v tématu Testdll2 .cpp v ukázce MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

Dynamické vytváření objektů MFC název knihovny MFC je podobná. Mechanismus serializace objektu knihovny MFC musí mít všechny `CRuntimeClass` registrované objekty tak, aby mohl rekonstruovat dynamicky vytvořením objektů jazyka C++ vyžaduje typu založeného na co byla uložena dříve.

V případě ukázky MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk), seznamu vypadá přibližně takto:

```
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE
               |                      |
          TESTDLL2.DLL           TESTDLL2.DLL
               |                      |
          TESTDLL1.DLL           TESTDLL1.DLL
               |                      |
           MFCOxxD.DLL                |
               |                      |
           MFCDxxD.DLL                |
               |                      |
            MFCxxD.DLL            MFCxx.DLL
```

kde *xx* je číslo verze; například 42 představuje verze 4.2.

Knihovny MFCxx.dll je obvykle poslední v seznamu prostředků a třídy. Knihovny MFCxx.dll zahrnuje všechny standardní prostředky MFC, včetně řetězce výzev pro všechny identifikátory standardních příkazů. Uvedení na konci seznamu umožňuje knihovny DLL a klient samotná aplikace není k dispozici vlastní kopii standardní prostředky MFC, ale místo toho spoléhají na sdílené prostředky do knihovny MFCxx.dll.

Nevýhodou je nutné mít na paměti, s jakou ID nebo názvy vyberete slučování prostředky a třídy názvů všech knihoven DLL do oboru názvů klientské aplikace má.

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) ukázka spravuje sdílený prostředek oboru názvů pomocí více souborů záhlaví.

Pokud vaše MFC – rozšiřující knihovny DLL je potřeba udržovat doplňující data pro každou aplikaci, lze odvodit novou třídu z **CDynLinkLibrary** a vytvořte jej v `DllMain`. Při spuštění, knihovny DLL můžete zkontrolovat aktuální aplikace seznam **CDynLinkLibrary** objekty, abyste našli ten konkrétní rozšiřující knihovny MFC DLL.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializace rozšiřující knihovny DLL MFC](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Tipy k používání souborů sdílených prostředků](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Viz také:

[Vytvoření knihovny DLL jazyka C/C++ v sadě Visual Studio](dlls-in-visual-cpp.md)
