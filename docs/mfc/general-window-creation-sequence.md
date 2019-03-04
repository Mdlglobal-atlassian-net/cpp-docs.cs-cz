---
title: Obecná posloupnost vytvoření okna
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 949cf72910654b502ca4b57be72bedc2db63c315
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269224"
---
# <a name="general-window-creation-sequence"></a>Obecná posloupnost vytvoření okna

Při vytváření okna vlastní, jako je například podřízená okna rozhraní používá mnohem stejně jako, který je popsáno v [vytváření dokumentů/zobrazení](../mfc/document-view-creation.md).

Třídy oken poskytovaných MFC využívají [dvoufázová konstrukce](../mfc/one-stage-and-two-stage-construction-of-objects.md). To znamená, že při vyvolání jazyka c++ **nové** operátor konstruktoru přiděluje a inicializuje objekt jazyka C++ ale nevytvoří odpovídající okno Windows. Který se následně provádí voláním [vytvořit](../mfc/reference/cwnd-class.md#create) členské funkce objektu okno.

`Create` Členská funkce je v okně Windows a ukládá jeho `HWND` v objekt jazyka C++ veřejné datový člen [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create` poskytuje dokončení flexibilitu prostřednictvím vytváření parametry. Před voláním `Create`, možná budete chtít zaregistrovat třídy okna s globální funkce [afxregisterwndclass –](../mfc/reference/application-information-and-management.md#afxregisterwndclass) nastavit ikonu a třída styly pro rámec.

Oken s rámečkem, můžete použít [loadframe –](../mfc/reference/cframewnd-class.md#loadframe) členskou funkci místo `Create`. `LoadFrame` Díky Windows okno s menším počtem parametrů. Získá mnoho výchozí hodnoty ze zdrojů, včetně titulek rámce, ikony, tabulky akcelerátorů a nabídky.

> [!NOTE]
>  Ikona, tabulky akcelerátorů a prostředky nabídky musí mít společné ID prostředku, jako například **IDR_MAINFRAME**, aby se načetl loadframe –.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Objekty oken](../mfc/window-objects.md)

- [Registrace tříd"oken"](../mfc/registering-window-classes.md)

- [Zničení objektů oken](../mfc/destroying-window-objects.md)

- [Vytváření oken s rámečkem v dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Viz také:

[Vytváření oken](../mfc/creating-windows.md)
