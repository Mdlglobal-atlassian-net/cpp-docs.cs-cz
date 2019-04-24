---
title: Třídy šablony dokumentu
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 2589bc8f04e791f73529af91ffb148c2c717cd08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164982"
---
# <a name="document-template-classes"></a>Třídy šablony dokumentu

Objekty šablony dokumentu koordinovat vytvoření dokumentu, zobrazení a objekty oken rámce při vytváření nového dokumentu nebo zobrazení je vytvořeno.

[CDocTemplate –](../mfc/reference/cdoctemplate-class.md)<br/>
Základní třída pro šablony dokumentů. Tato třída se nikdy nepoužívejte přímo. Místo toho použít jeden z jiné třídy šablony dokumentu odvozen z této třídy.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Šablona pro dokumenty v rozhraní více dokumentů (MDI). Aplikace MDI může mít několik dokumentů, otevřete v čase.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Šablona pro dokumenty v rozhraní jednoho dokumentu (SDI). Aplikace SDI mít pouze jeden dokument otevřete v čase.

## <a name="related-class"></a>Související třídy

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Struktury předávány šablonu dokumentu pro funkce vytvoření okna pro koordinaci vytváření objektů dokumentů, zobrazení a oken s rámečkem.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
