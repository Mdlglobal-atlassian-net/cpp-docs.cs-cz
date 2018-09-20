---
title: Obecná posloupnost vytvoření okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9336e5fa19b373f07c54e758a6f939bbc63e50ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432786"
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

## <a name="see-also"></a>Viz také

[Vytváření oken](../mfc/creating-windows.md)

