---
title: 'MIDL – stránky vlastností: Upřesnit | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f87518c23848cea91a3e3c48361aa0a63fa88a2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33330801"
---
# <a name="midl-property-pages-advanced"></a>MIDL – stránky vlastností: Upřesnit
**Upřesnit** stránka vlastností v **MIDL** složky určuje následující volby kompilátoru MIDL:  
  
-   Povolit kontrolu chyb ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Kontrola přidělení ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Kontrola hranice ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Kontrola rozsahu výčtu ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Kontrola ukazatelů referencí ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Zkontrolujte, zda se zakázaným inzerováním Data ([/Error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   Ověření parametrů ([/ robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)) *  
  
-   Zarovnání členů struktury ([/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388))  
  
-   Přesměrujte výstup ([/o](http://msdn.microsoft.com/library/windows/desktop/aa367351))  
  
-   Předběžné zpracování možnosti jazyka C ([/cpp_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318))  
  
-   Nedefinované Definice preprocesoru ([/U](http://msdn.microsoft.com/library/windows/desktop/aa367373))  
  
 \* / Robustní je jenom pro použití při vytváření pro Windows 2000 nebo novější počítač. Pokud projekt knihovny ATL a chcete použít / robust, změňte tento řádek v souboru dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 Informace o tom, jak získat přístup **Upřesnit** stránka vlastností v **MIDL** složky, najdete v části [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
 Informace o tom, jak programového přístupu MIDL pro projekty C++ najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.  
  
## <a name="see-also"></a>Viz také  
 [MIDL – stránky vlastností](../ide/midl-property-pages.md)