---
title: 'Rozšiřující knihovny DLL: Přehled'
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221368"
---
# <a name="mfc-extension-dlls-overview"></a>Rozšiřující knihovny MFC DLL: Přehled

Rozšiřující knihovna MFC DLL je knihovna DLL, která obvykle implementuje opakovaně použitelné třídy odvozené z existujících tříd knihovna Microsoft Foundation Class. Rozšiřující knihovny DLL knihovny MFC jsou sestaveny pomocí verze knihovny MFC dynamického propojení (označované také jako sdílená verze knihovny MFC). Knihovny DLL rozšíření MFC mohou používat pouze spustitelné soubory knihovny MFC (buď aplikace nebo běžné knihovny MFC DLL), které jsou vytvořeny pomocí sdílené verze knihovny MFC. Pomocí knihovny DLL rozšíření knihovny MFC můžete odvodit nové vlastní třídy z knihovny MFC a následně nabízet tuto rozšířenou verzi knihovny MFC aplikacím, které volají vaši DLL knihovnu.

Rozšiřující knihovny DLL lze také použít pro předávání objektů odvozených od knihovny MFC mezi aplikací a knihovnou DLL. Členské funkce přidružené k předanému objektu existují v modulu, ve kterém byl objekt vytvořen. Vzhledem k tomu, že tyto funkce jsou správně exportovány při použití sdílené knihovny DLL verze knihovny MFC, je možné volně předat ukazatele objektů MFC nebo MFC odvozené od aplikace a rozšiřujících knihoven DLL MFC, které načte.

Příklad knihovny DLL, která splňuje základní požadavky knihovny DLL rozšíření MFC, naleznete v tématu [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)Sample MFC. Zejména se podívejte na soubory Testdll1. cpp a Testdll2. cpp.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializace knihovny DLL rozšíření MFC](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [MFC – rozšiřující knihovny DLL](extension-dlls.md)

- [Používání databázových, OLE a soketových rozšiřujících knihoven MFC DLL v běžných knihovnách MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Knihovny DLL mimo MFC – přehled](non-mfc-dlls-overview.md)

- [Běžné knihovny MFC DLL staticky propojené s knihovnou MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Vytvoření knihovny MFC DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Viz také

[Druhy knihoven DLL](kinds-of-dlls.md)
