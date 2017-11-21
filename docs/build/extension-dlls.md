---
title: "Rozšiřující knihovny DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afxdll
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f42c738983cb0d2017614279a35ab79ae677fb1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-extension-dlls"></a>MFC – rozšiřující knihovny DLL
MFC DLL je rozšíření knihovny DLL, která implementuje použitelné třídy odvozené z existujících tříd Microsoft Foundation Class Library.  
  
 Knihovnu DLL má následující funkce a požadavky:  
  
-   Spustitelný soubor klienta musí být aplikace MFC kompilovat s `_AFXDLL` definované.  
  
-   Knihovnu DLL mohou sloužit také běžné MFC knihovny DLL dynamicky propojené s knihovnou MFC.  
  
-   MFC – rozšiřující knihovny DLL má kompilovat s `_AFXEXT` definované. Vynutí se tak `_AFXDLL` také definovat a zajistí, že správné deklarace jsou získány z MFC hlavičky souborů. Také zajistí, že `AFX_EXT_CLASS` je definován jako `__declspec(dllexport)` při vytváření knihovny DLL, který je nezbytný, pokud použijete tento makro pro deklarování tříd ve vaší MFC – rozšiřující knihovny DLL.  
  
-   MFC – rozšiřující knihovny DLL nevytvoří instanci třídy odvozené od `CWinApp`, ale se spoléhají na klientská aplikace (nebo DLL) k poskytnutí tohoto objektu.  
  
-   MFC – rozšiřující knihovny DLL by měl, ale poskytovat `DllMain` funkce a proveďte všechny nezbytné inicializace.  
  
 Rozšiřující knihovny DLL jsou vytvořeny pomocí knihovny DLL verze knihovny MFC (také označovaný jako sdílený verze knihovny MFC). Pouze spustitelné soubory knihovny MFC (aplikace nebo běžné knihovny MFC DLL), jsou integrované s sdílená verze knihovny MFC můžete použít knihovnu DLL. Klientská aplikace i MFC – rozšiřující knihovny DLL musí používat stejnou verzi nástroje MFCx0.dll. S příponou MFC DLL lze odvodit nové vlastní třídy z rozhraní MFC a pak nabízet toto rozšířené verze knihovny MFC k aplikacím, které volání knihovny DLL.  
  
 Rozšiřující knihovny DLL mohou sloužit také pro předávání odvozené knihovny MFC objektů mezi aplikací a knihovny DLL. Členské funkce přidružený objekt předaný existovat v modulu, kde se objekt vytvořil. Protože tyto funkce správně exportují se při použití sdílené knihovny DLL verze knihovny MFC, můžete volně předat MFC nebo odvozené knihovny MFC objekt ukazatele mezi aplikací a MFC – rozšiřující knihovny DLL načte.  
  
 Knihovnu DLL používá sdílená verze knihovny MFC stejným způsobem, jakým aplikace používá sdílenou knihovnu DLL verze knihovny MFC, několik dalších aspektů:  
  
-   Nemá `CWinApp`-odvozené objektu. Musí pracovat `CWinApp`-odvozené objekt klientské aplikace. To znamená, že klientská aplikace vlastní hlavní message pump, nečinné smyčky a tak dále.  
  
-   Zavolá `AfxInitExtensionModule` v jeho `DllMain` funkce. Zkontrolovat návratovou hodnotu této funkce. Pokud je nulová hodnota vrácená z `AfxInitExtensionModule`, vrátí 0 z vaší `DllMain` funkce.  
  
-   Vytvoří **CDynLinkLibrary** během inicializace objektu, pokud rozšíření MFC DLL chce exportovat `CRuntimeClass` objekty nebo prostředky pro aplikaci.  
  
 Před verzí 4.0 knihovny MFC byl tento typ knihovny DLL označuje AFXDLL. AFXDLL odkazuje `_AFXDLL` symbol preprocesoru, který je definován při vytváření knihovny DLL.  
  
 Import knihoven pro sdílené verze knihovny MFC jsou pojmenovány podle zásady, popsané v [konvence vytváření názvů pro knihovny MFC DLL](../build/naming-conventions-for-mfc-dlls.md). Visual C++ dodává připravené verze knihovny MFC DLL plus číslo z non - MFC DLL, kterou můžete použít a distribuovat s vašimi aplikacemi. Ty jsou popsané v souboru Redist.txt, který je nainstalován do složky, Program Files\Microsoft Visual Studio.  
  
 Pokud exportujete pomocí souborů .def, vložte následující kód na začátku a konci hlavičkový soubor:  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Tyto čtyři řádky zajistí, že váš kód se zdařilo pro knihovnu DLL. Opouštění těchto čtyř řádků může způsobit vaše DLL kompilovat nebo nesprávně propojení.  
  
 Pokud potřebujete předat knihovny MFC nebo ukazatele na objekt odvozené knihovny MFC z knihovny MFC DLL, knihovny DLL nebo by měly být knihovnu DLL. Členské funkce přidružený objekt předaný existovat v modulu, kde se objekt vytvořil. Protože tyto funkce správně exportují se při použití sdílené knihovny DLL verze knihovny MFC, můžete volně předat MFC nebo odvozené knihovny MFC objekt ukazatele mezi aplikací a MFC – rozšiřující knihovny DLL načte.  
  
 Z důvodu pozměnění a export problémy název C++ seznamu export z rozšíření MFC DLL může být liší ladění a prodejní verze stejné knihovny DLL a knihovny DLL pro různé platformy. Verze knihovny MFCx0.dll má přibližně 2 000 exportovaných vstupních bodů; ladicí verze knihovny MFCx0D.dll má přibližně 3 000 exportovaný vstupní body.  
  
## <a name="memory-management"></a>Správa paměti  
 MFCx0.dll a všechny MFC – rozšiřující knihovny DLL načten do adresního prostoru klientskou aplikaci používat stejné přidělení paměti, načítání prostředků a jiné globální stavy knihovny MFC jako kdyby byly ve stejné aplikaci. To je důležité, protože regulární knihovny DLL MFC a knihovny MFC DLL přesný opak a každou knihovnu DLL přidělování mimo svůj vlastní fond paměti k dispozici.  
  
 Pokud knihovnu DLL přidělí paměť, že paměť můžete libovolně kombinovat s jakýkoliv jiný objekt přidělené aplikace. Také v případě selhání aplikace, která propojuje ke knihovně MFC ochranu operačního systému udržuje integritu jiné aplikace MFC sdílení knihovny DLL.  
  
 Podobně jako jiné globální stavy knihovny MFC, jako je aktuální spustitelný soubor načtení zdrojů, jsou také sdílené mezi klientská aplikace a všechny MFC – knihovny DLL rozšíření a také MFCx0.dll.  
  
## <a name="sharing-resources-and-classes"></a>Sdílení prostředků a třídy  
 Export zdrojů se provádí pomocí seznamu prostředků. Každá aplikace obsahuje jednotlivě propojený seznam **CDynLinkLibrary** objekty. Při hledání prostředku, většina standardní MFC implementací, které načíst prostředky, nejprve vyhledává v aktuálním modulu prostředků (`AfxGetResourceHandle`) a pokud není nalezena prostředku provede seznam **CDynLinkLibrary** objekty došlo k pokusu o načtení požadovaný prostředek.  
  
 Procházení seznamem má nevýhody, že je něco pomalejší a vyžaduje správu rozsahů ID prostředků. Má výhodu v podobě, klientská aplikace, která obsahuje odkazy na několik knihoven DLL rozšíření MFC můžete jakémukoli prostředku, poskytuje knihovnu DLL bez nutnosti zadávat popisovač instance knihovny DLL. `AfxFindResourceHandle`rozhraní API slouží k procházení seznamu prostředků a hledat odpovídající shody. Přebírá název a typ prostředku a vrátí popisovač prostředku, kde byl nalezen první (nebo hodnota NULL).  
  
 Pokud nechcete načíst pouze prostředky z konkrétní místa a provede seznamu, použijte funkce `AfxGetResourceHandle` a `AfxSetResourceHandle` uložte starý popisovač a nastavit nový popisovač. Ujistěte se, že obnovit starý popisovač prostředku, pak se vraťte do klientské aplikace. Příklad použití tohoto přístupu explicitně načíst nabídky, naleznete v části sada Testdll2 v ukázce MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).  
  
 Dynamické vytváření objektů MFC MFC název je podobný. Mechanismus deserializace objektu knihovny MFC musí mít všechny `CRuntimeClass` objekty registraci tak, aby ji můžete obnovit dynamicky vytvořením objektů jazyka C++ z požadovaného typu, založené na co byla uložena dříve.  
  
 V případě ukázka MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk), seznamu vypadá podobně jako:  
  
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
  
 kde *xx* je číslo verze; například 42 představuje verzi 4.2.  
  
 MFCxx.dll je obvykle poslední na prostředek a seznam tříd. MFCxx.dll zahrnuje všechny standardní prostředky MFC, včetně řetězců pro všechny identifikátory standardních příkazů. Jeho umístění na konci seznamu umožňuje knihovny DLL a klienta vlastní aplikace není k dispozici vlastní kopii standardní prostředky MFC, ale místo toho spoléhají na sdílené prostředky v MFCxx.dll.  
  
 Slučování prostředky a názvy tříd všech knihoven DLL do oboru názvů klientské aplikace má nevýhodou vyžadující, abyste pečlivě s co ID nebo názvy, které vyberete.  
  
 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) ukázka spravuje obor názvů sdílený prostředek pomocí více záhlaví souborů.  
  
 Pokud vaše MFC – rozšiřující knihovny DLL musí udržovat doplňující data pro každou aplikaci, lze odvodit novou třídu z **CDynLinkLibrary** a vytvořte ji v `DllMain`. Při spuštění, knihovnu DLL zkontrolovat seznam aktuální aplikace **CDynLinkLibrary** objekty, které chcete vyhledat konkrétní MFC rozšiřující knihovny DLL.  
  
### <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Inicializovat knihovnu DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Tipy k používání souborů sdílených prostředků](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [DLL verze knihovny MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [Regulární knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regulární knihovny MFC DLL dynamicky propojené s MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Pomocí databáze OLE a Sockets MFC rozšiřující knihovny DLL v běžných knihovnách DLL knihovny MFC](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)