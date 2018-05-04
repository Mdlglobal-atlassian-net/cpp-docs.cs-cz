---
title: Regulární knihovny MFC DLL staticky propojené do MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48fdfb0b10541c1643ec49038e29cfa60c633d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>Regulární knihovny MFC DLL staticky propojené do MFC
Knihovny DLL, která používá MFC interně je běžný, které MFC DLL staticky propojené do MFC a exportovaných funkcí v knihovně DLL lze volat pomocí knihovny MFC nebo mimo MFC spustitelné soubory. Podle názvu, popisu, tento druh DLL vytvořená s využitím staticky propojené verze knihovny MFC. Funkce jsou obvykle exportovány z běžný MFC DLL pomocí standardní rozhraní jazyka. Příklad toho, jak zapsat, vytvářet a používat běžné knihovny MFC DLL v tématu vzorku [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).  
  
 Všimněte si, že pojem USRDLL se již nepoužívá v dokumentaci k Visual C++. Běžné knihovny DLL MFC, který je staticky propojené do MFC má stejné vlastnosti jako dosavadní USRDLL.  
  
 Regulární knihovny DLL MFC staticky propojené do MFC, má následující funkce:  
  
-   Spustitelný soubor klienta může být napsán v jakýkoli jazyk, který podporuje použití knihovny DLL (C, C++, Pascal, Visual Basic a tak dále); nemá být aplikace knihovny MFC.  
  
-   Knihovny DLL můžete propojit stejné staticky propojené knihovny MFC používané aplikacemi. Je již nebude samostatnou verzi knihovny statický odkaz pro knihovny DLL.  
  
-   Před verzí 4.0 knihovny MFC USRDLL poskytovaly stejný typ funkce jako regulární knihovny MFC DLL staticky propojené do MFC. Od verze Visual C++ verze 4.0, pojem USRDLL je zastaralé.  
  
 Regulární knihovny DLL MFC staticky propojené do MFC, má následující požadavky:  
  
-   Tento typ knihovny DLL musí vytvořit instanci třídy odvozené od `CWinApp`.  
  
-   Tento typ používá DLL `DllMain` poskytované MFC. Umístit všechny kód inicializace specifické knihovny DLL `InitInstance` funkce a ukončení kód člena v `ExitInstance` jako běžné aplikace knihovny MFC.  
  
-   Přestože se termín je USRDLL zastaralý, je nutné definovat "**_USRDLL**" na příkazovém řádku kompilátoru. Tato definice určuje, které deklarace jsou získány z MFC hlavičky souborů.  
  
 Regulární knihovny MFC DLL musí mít `CWinApp`-odvozené třídy a jeden objekt třídy aplikace, stejně jako aplikace knihovny MFC. Ale `CWinApp` objekt knihovny DLL nemá hlavní zprávy odeslané, stejně jako `CWinApp` objektu aplikace.  
  
 Všimněte si, že `CWinApp::Run` mechanismus se nevztahuje na knihovnu DLL, protože aplikace vlastní hlavní message pump. Pokud knihovnu DLL otevře nemodální dialogová okna nebo má své vlastní okno hlavního rámce, čerpadlo hlavní zpráv aplikace musí volat rutinu exportované sadou knihovnu DLL, která volá `CWinApp::PreTranslateMessage` členské funkce objektu aplikace knihovnu DLL.  
  
 Příklad této funkce najdete v tématu na ukázku DLLScreenCap.  
  
 Symboly jsou obvykle exportovány z běžný MFC DLL pomocí standardní rozhraní jazyka. Prohlášení o funkce exportované z běžné knihovny MFC DLL by vypadat přibližně takto:  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Všechny přidělení paměti v rámci běžné knihovny MFC DLL může zůstat v rámci knihovny DLL; Knihovna DLL by neměla předat nebo přijímat volání spustitelnému souboru některé z následujících:  
  
-   Ukazatelé na objekty MFC  
  
-   Ukazatelé na přidělenou paměť knihovnou MFC  
  
 Pokud potřebujete provádět žádnou z výše uvedených nebo potřebujete předat objekt odvozené MFC mezi voláním spustitelného souboru a knihovny DLL, musíte sestavit knihovnu DLL.  
  
 Je bezpečné předat ukazatelé na paměti, které byly přiděleny podle běhové knihovny jazyka C mezi aplikací a knihovny DLL pouze v případě, že můžete vytvořit kopii data. Nesmí odstranit nebo změnit velikost těchto ukazatelů nebo je použít bez vytváření kopie paměti.  
  
 Knihovny DLL, která je staticky propojené do MFC nelze propojit také dynamicky sdílené knihovny MFC DLL. Knihovny DLL, která je staticky propojené do MFC je dynamicky vázána na aplikace, stejně jako jiné knihovny DLL; aplikace se propojit k němu stejně jako jiné knihovny DLL.  
  
 Standardní staticky propojené knihovny MFC jsou pojmenované podle zásady, popsané v [zásady vytváření názvů pro knihovny MFC DLL](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Však MFC verze 3.0 a novější, je už není nutné ručně zadat linkeru verze knihovny MFC, kterou chcete propojit v. Soubory hlaviček MFC místo toho automaticky určit, správná verze knihovny MFC propojení v závislosti na preprocesor definuje, jako například  **\_ladění** nebo **_UNICODE**. Soubory hlaviček MFC Přidání direktivy /DEFAULTLIB propojovací program pro odkaz na konkrétní verzi knihovny MFC.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Inicializovat běžné knihovny MFC DLL](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Použití prostředí MFC jako součásti knihovny DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Vytvoření knihovny MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
-   [Běžné knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Viz také  
 [Typy knihoven DLL](../build/kinds-of-dlls.md)