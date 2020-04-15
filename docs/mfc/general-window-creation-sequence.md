---
title: Obecná posloupnost vytvoření okna
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364275"
---
# <a name="general-window-creation-sequence"></a>Obecná posloupnost vytvoření okna

Při vytváření vlastního okna, například podřízeného okna, framework používá téměř stejný proces, který je popsán v [dokumentu nebo zobrazit vytvoření](../mfc/document-view-creation.md).

Všechny třídy oken poskytované knihovnou MFC používají [dvoustupňovou výstavbu](../mfc/one-stage-and-two-stage-construction-of-objects.md). To znamená, že během vyvolání **nového** operátoru Jazyka C++ konstruktor přiděluje a inicializuje objekt jazyka C++, ale nevytváří odpovídající okno systému Windows. To se provádí později voláním [Vytvořit](../mfc/reference/cwnd-class.md#create) členská funkce objektu okna.

Členská `Create` funkce vytvoří okno systému Windows a uloží jeho `HWND` do veřejného datového člena objektu C++ [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create`poskytuje úplnou flexibilitu nad parametry tvorby. Před `Create`voláním můžete chtít zaregistrovat třídu okna s globální funkcí [AfxRegisterWndClass,](../mfc/reference/application-information-and-management.md#afxregisterwndclass) abyste nastavili styly ikon a tříd pro rámec.

Pro okna rámců můžete [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) místo `Create`. `LoadFrame`vytvoří okno systému Windows s menším počtem parametrů. Získá mnoho výchozích hodnot z prostředků, včetně titulku rámce, ikony, tabulky akcelerátoru a nabídky.

> [!NOTE]
> Vaše ikona, tabulka akcelerátoru a zdroje nabídek musí mít společné ID prostředků, například **IDR_MAINFRAME**, aby je loadframe načetl.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Objekty oken](../mfc/window-objects.md)

- [Registrovací okno "třídy"](../mfc/registering-window-classes.md)

- [Zničení okenních objektů](../mfc/destroying-window-objects.md)

- [Vytváření oken rámečků dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Viz také

[Vytváření oken](../mfc/creating-windows.md)
