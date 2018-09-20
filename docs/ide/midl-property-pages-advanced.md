---
title: 'MIDL – stránky vlastností: Upřesnit | Dokumentace Microsoftu'
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
ms.openlocfilehash: 11c7d4b437e77e5acfe363fd3b4125477eceb0f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394960"
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

Informace o tom, jak získat přístup k **Upřesnit** stránku vlastností v **MIDL** složky, najdete v článku [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

Informace o tom, jak programově přistupovat k MIDL pro projekty C++, naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>Viz také

[MIDL – stránky vlastností](../ide/midl-property-pages.md)