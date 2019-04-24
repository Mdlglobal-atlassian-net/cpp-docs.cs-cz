---
title: Tisk a náhled tisku
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 70740922ec7f2030d14eebee72144a373550aacc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218713"
---
# <a name="printing-and-print-preview"></a>Tisk a náhled tisku

MFC podporuje tisku a tiskového náhledu pro dokumenty vaší aplikace prostřednictvím třídy [CView](../mfc/reference/cview-class.md). Pro základní tisku a tiskového náhledu, jednoduše potlačit zobrazení třídy [OnDraw](../mfc/reference/cview-class.md#ondraw) členská funkce, které musíte udělat i přesto. Tuto funkci lze nakreslit na zobrazení na obrazovce, kontext zařízení tiskárny pro skutečný tiskárny, nebo do kontextu zařízení, která simuluje tiskárny na obrazovce.

Můžete také přidat kód pro správu Tisk vícestránkového dokumentu a ve verzi preview, přejdete tisknutých dokumentů a přidávání hlaviček a zápatí do nich.

Tato řada článků popisuje, jak tisk je implementovaná v třídy knihovny MFC (Microsoft Foundation) a tom, jak využít výhod již zahrnutým v rámci architektura pro tisk. V článcích také vysvětlují, jak MFC podporuje snadné provádění funkce náhledu tisku a jak můžete používat a upravovat, které tuto funkci.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Tisk](../mfc/printing.md)

- [Architektura náhledu tisku](../mfc/print-preview-architecture.md)

- [Ukázka](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
