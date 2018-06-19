---
title: 'Rozšiřující knihovny DLL: Přehled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bd851b9335e2b1ecffc8873590f176d7ebb2205
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367817"
---
# <a name="mfc-extension-dlls-overview"></a>MFC – rozšiřující knihovny DLL: Přehled
MFC DLL je rozšíření knihovny DLL, která implementuje použitelné třídy odvozené z existujících tříd Microsoft Foundation Class Library. MFC – knihovny DLL rozšíření jsou vytvořeny pomocí knihovny DLL verze knihovny MFC (také označovaný jako sdílený verze knihovny MFC). Pouze spustitelné soubory knihovny MFC (aplikace nebo běžné knihovny MFC DLL), jsou integrované s sdílená verze knihovny MFC můžete použít knihovnu DLL. S příponou MFC DLL lze odvodit nové vlastní třídy z rozhraní MFC a pak nabízet toto rozšířené verze knihovny MFC k aplikacím, které volání knihovny DLL.  
  
 Rozšiřující knihovny DLL mohou sloužit také pro předávání odvozené knihovny MFC objektů mezi aplikací a knihovny DLL. Členské funkce přidružený objekt předaný existovat v modulu, kde se objekt vytvořil. Protože tyto funkce správně exportují se při použití sdílené knihovny DLL verze knihovny MFC, můžete volně předat MFC nebo odvozené knihovny MFC objekt ukazatele mezi aplikací a MFC – rozšiřující knihovny DLL načte.  
  
 Příklad knihovny DLL, která splňuje základní požadavky pro knihovnu DLL, naleznete v části ukázka MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). Podívejte se na konkrétní na soubory Testdll1.cpp a Testdll2.cpp.  
  
 Všimněte si, že pojem AFXDLL se již nepoužívá v dokumentaci k Visual C++. Knihovnu DLL má stejné vlastnosti jako dřívější AFXDLL.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Inicializovat knihovnu DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [MFC – rozšiřující knihovny DLL](../build/extension-dlls.md)  
  
-   [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Knihovny DLL mimo MFC – přehled](../build/non-mfc-dlls-overview.md)  
  
-   [Regulární knihovny MFC DLL staticky propojené do MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regulární knihovny MFC DLL dynamicky propojené s MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Vytvoření knihovny MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
## <a name="see-also"></a>Viz také  
 [Typy knihoven DLL](../build/kinds-of-dlls.md)