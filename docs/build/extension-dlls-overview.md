---
title: 'Rozšiřující knihovny DLL: Přehled'
ms.date: 11/04/2016
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ab9b980cbb3e89eebee945e90c54f23d6717a1a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196726"
---
# <a name="mfc-extension-dlls-overview"></a>MFC – rozšiřující knihovny DLL: Přehled

MFC – rozšiřující knihovny DLL je knihovnu DLL, která se obvykle implementují opakovaně použitelné třídy odvozené z existujících tříd knihovny Microsoft Foundation Class. Rozšiřující knihovny DLL MFC jsou vytvořené pomocí knihovny DLL verze knihovny MFC (označované také jako sdílených verzí knihovny MFC). Pouze spustitelné soubory knihovny MFC (aplikace nebo běžných knihovnách MFC DLL), které jsou integrovány s sdílených verzí knihovny MFC můžete použít rozšiřující knihovny DLL MFC. S rozšiřující knihovny DLL MFC lze odvozovat nové vlastní třídy knihovny MFC a potom nabídnout tato rozšířená verze knihovny MFC k aplikacím, které volají vaši knihovnu DLL.

Rozšiřující knihovny DLL lze použít také pro předávání mezi aplikací a knihovny DLL MFC odvozené objekty. Členské funkce související s předaným objektem existovat v modulu, ve kterém byl objekt vytvořen. Protože tyto funkce se správně vyexportovala při použití sdílené knihovny DLL verze knihovny MFC, můžete předat volně knihovny MFC nebo knihovny MFC odvozenému objektu ukazatele mezi aplikací a MFC – rozšiřující knihovny DLL načte.

Příklad knihovny DLL, která splňuje základní požadavky pro rozšiřující knihovny DLL MFC, najdete v ukázce MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). Konkrétně se podívejte na Testdll1.cpp a Testdll2.cpp soubory.

Všimněte si, že v dokumentaci k Visual C++ se již nepoužívá termín AFXDLL. Rozšiřující knihovny DLL MFC má stejné vlastnosti jako dřívější AFXDLL.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializace rozšiřující knihovny DLL MFC](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [MFC – rozšiřující knihovny DLL](extension-dlls.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Knihovny DLL mimo MFC: Přehled](non-mfc-dlls-overview.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Vytváření knihovny MFC DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Viz také:

[Typy knihoven DLL](kinds-of-dlls.md)
