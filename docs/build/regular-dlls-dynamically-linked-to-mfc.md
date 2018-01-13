---
title: "Regulární knihovny MFC DLL dynamicky propojené s MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930d56f7bc296225e6fefcf92e49087a2aed99cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Regulární knihovny MFC DLL dynamicky propojené s MFC
Knihovny DLL, která používá MFC interně je běžný, které MFC DLL dynamicky propojené s MFC a exportovaných funkcí v knihovně DLL lze volat pomocí knihovny MFC nebo mimo MFC spustitelné soubory. Podle názvu, popisu, tento druh DLL vytvořená s využitím knihovna DLL verze knihovny MFC (také označovaný jako sdílený verze knihovny MFC). Funkce jsou obvykle exportovány z běžný MFC DLL pomocí standardní rozhraní jazyka.  
  
 Je nutné přidat `AFX_MANAGE_STATE` makro na začátku všech exportovaných funkcí v běžných knihovnách DLL MFC, která dynamicky propojené s knihovnou MFC na aktuální stav modulu nastaveno pro knihovnu DLL. To se provádí přidáním následující kód do začátku funkce exportované z knihovny DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Běžný MFC DLL dynamicky propojené s MFC má následující funkce:  
  
-   Toto je nový typ knihovny DLL zaváděné Visual C++ 4.0.  
  
-   Spustitelný soubor klienta může být napsán v jakýkoli jazyk, který podporuje použití knihovny DLL (C, C++, Pascal, Visual Basic a tak dále); nemá být aplikace knihovny MFC.  
  
-   Na rozdíl od staticky propojené regulární MFC DLL je tento typ knihovny DLL dynamicky propojené s knihovnou MFC DLL (také označované jako sdílená knihovna MFC DLL).  
  
-   Import knihovny MFC propojená s tímto typem knihovny DLL je stejný jako ten, použít pro rozšíření MFC – knihovny DLL nebo aplikace pomocí knihovny MFC DLL: .lib MFCxx (D).  
  
 Běžný MFC DLL dynamicky propojené s MFC má následující požadavky:  
  
-   Tyto knihovny jsou kompilovat s **_AFXDLL** definované, stejně jako spustitelné soubory, které je dynamicky propojené s knihovnou MFC DLL. Ale **_USRDLL** je také definován, stejně jako regulární MFC DLL, která je staticky propojené do MFC.  
  
-   Tento typ knihovny DLL musí vytvořit instanci `CWinApp`-odvozené třídy.  
  
-   Tento typ používá DLL `DllMain` poskytované MFC. Umístit všechny kód inicializace specifické knihovny DLL `InitInstance` funkce a ukončení kód člena v `ExitInstance` jako běžné aplikace knihovny MFC.  
  
 Protože používá tento druh DLL verze knihovny MFC, musíte nastavit aktuální stav modulu explicitně na jeden z knihovny DLL. Chcete-li to provést, použijte [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) makro na začátku každé funkce exportovat z knihovny DLL.  
  
 Regulární knihovny MFC DLL musí mít `CWinApp`-odvozené třídy a jeden objekt třídy aplikace, stejně jako aplikace knihovny MFC. Ale `CWinApp` objekt knihovny DLL nemá hlavní zprávy odeslané, stejně jako `CWinApp` objektu aplikace.  
  
 Všimněte si, že `CWinApp::Run` mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní message pump. Pokud vaše knihovna DLL vyvolá nemodální dialogová okna nebo má své vlastní okno hlavního rámce, hlavní "message pump" vaší aplikace musí volat rutinu Export knihovny DLL, která volá `CWinApp::PreTranslateMessage`.  
  
 Umístěte všechny inicializace specifické knihovny DLL v `CWinApp::InitInstance` – členská funkce jako normální MFC aplikaci. `CWinApp::ExitInstance` Členské funkce vaše `CWinApp` odvozené třídy je volána z MFC poskytuje `DllMain` funkce před uvolněním knihovnu DLL.  
  
 S vaší aplikací je nutné distribuovat sdílené knihovny DLL MFCx0.dll a Msvcr*0.dll (nebo podobné soubory).  
  
 Knihovny DLL dynamicky propojené s knihovnou MFC nemůže být staticky propojena s knihovnou MFC. Aplikace odkaz regulární MFC – knihovny DLL dynamicky propojené s MFC ho stejně jako jiné knihovny DLL.  
  
 Symboly jsou obvykle exportovány z běžný MFC DLL pomocí standardní rozhraní jazyka. Prohlášení o funkce exportované z běžné knihovny MFC DLL vypadá přibližně takto:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Všechny přidělení paměti v rámci běžné knihovny MFC DLL může zůstat v rámci knihovny DLL; Knihovna DLL by neměla předat nebo přijímat volání spustitelnému souboru některé z následujících:  
  
-   Ukazatelé na objekty MFC  
  
-   Ukazatelé na přidělenou paměť knihovnou MFC  
  
 Pokud je třeba provádět žádnou z výše, nebo pokud potřebujete předat objekt odvozené MFC mezi voláním spustitelného souboru a knihovny DLL, je nutné vytvořit knihovnu DLL.  
  
 Je bezpečné předat ukazatelé na paměti, které byly přiděleny podle běhové knihovny jazyka C mezi aplikací a knihovny DLL pouze v případě, že můžete vytvořit kopii data. Nesmí odstranit nebo změnit velikost těchto ukazatelů nebo je použít bez vytváření kopie paměti.  
  
 Při vytváření běžné knihovny MFC DLL, která dynamicky odkazuje na knihovny MFC a budete muset použít makro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) ke správnému přepnutí stavu modulu MFC. To se provádí přidáním následující kód do začátku funkce exportované z knihovny DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 **AFX_MANAGE_STATE** makro není vhodné používat v běžných knihovnách DLL MFC, která buď staticky nebo MFC – rozšiřující knihovny DLL. Další informace najdete v tématu [Správa stavu dat modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md).  
  
 Příklad toho, jak zapsat, vytvářet a používat běžné knihovny MFC DLL v tématu vzorku [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Další informace o regulární knihovny MFC DLL, která dynamicky propojené s knihovnou MFC najdete v části s názvem "Převod DLLScreenCap na dynamicky odkaz s knihovnou MFC DLL" v přehledu příkladu.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Inicializovat běžné knihovny MFC DLL](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Stavy modulů běžné knihovny MFC DLL dynamicky propojené s MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [Správa dat stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## <a name="see-also"></a>Viz také  
 [Typy knihoven DLL](../build/kinds-of-dlls.md)