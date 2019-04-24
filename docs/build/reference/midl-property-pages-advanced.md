---
title: 'MIDL – stránky vlastností: Upřesnit'
ms.date: 11/04/2016
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
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
ms.openlocfilehash: 350563d140823910667812930f9283c7640cc1ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321472"
---
# <a name="midl-property-pages-advanced"></a>MIDL – stránky vlastností: Upřesnit

**Upřesnit** stránku vlastností v **MIDL** složky určuje následující možnosti kompilátoru MIDL:

- Povolit kontrolu chyb ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Kontrolovat přidělení paměti ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Kontrolovat rozsah ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Kontrolovat rozsah výčtu ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Kontrolovat referenční ukazatele ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Kontrolovat Data zástupných procedur ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Ověřit parametry ([/ robust](https://msdn.microsoft.com/library/windows/desktop/aa367363)) \*

- Zarovnání členů struktury ([/zp](https://msdn.microsoft.com/library/windows/desktop/aa367388))

- Přesměrovat výstup ([/o](https://msdn.microsoft.com/library/windows/desktop/aa367351))

- Možnosti předzpracování jazyka C ([/cpp_opt](https://msdn.microsoft.com/library/windows/desktop/aa367318))

- Zrušit Definice preprocesoru ([/U](https://msdn.microsoft.com/library/windows/desktop/aa367373))

\* / Robustní platí pouze pro použití při sestavování pro Windows 2000 nebo novější počítače. Pokud se sestavení projektu ATL a chcete použít / robust, změňte tento řádek v souboru dlldatax.c:

```
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM
to
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM
```

Informace o tom, jak získat přístup k **Upřesnit** stránku vlastností v **MIDL** složky, najdete v článku [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

Informace o tom, jak programově přistupovat k MIDL pro projekty C++, naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>Viz také:

[MIDL – stránky vlastností](midl-property-pages.md)
