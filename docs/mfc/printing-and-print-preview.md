---
title: Tisk a náhled tisku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aad5c69f6466ea8803cb466c5e5529f3dce1340
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374448"
---
# <a name="printing-and-print-preview"></a>Tisk a náhled tisku

MFC podporuje tisku a tiskového náhledu pro dokumenty vaší aplikace prostřednictvím třídy [CView](../mfc/reference/cview-class.md). Pro základní tisku a tiskového náhledu, jednoduše potlačit zobrazení třídy [OnDraw](../mfc/reference/cview-class.md#ondraw) členská funkce, které musíte udělat i přesto. Tuto funkci lze nakreslit na zobrazení na obrazovce, kontext zařízení tiskárny pro skutečný tiskárny, nebo do kontextu zařízení, která simuluje tiskárny na obrazovce.

Můžete také přidat kód pro správu Tisk vícestránkového dokumentu a ve verzi preview, přejdete tisknutých dokumentů a přidávání hlaviček a zápatí do nich.

Tato řada článků popisuje, jak tisk je implementovaná v třídy knihovny MFC (Microsoft Foundation) a tom, jak využít výhod již zahrnutým v rámci architektura pro tisk. V článcích také vysvětlují, jak MFC podporuje snadné provádění funkce náhledu tisku a jak můžete používat a upravovat, které tuto funkci.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Tisk](../mfc/printing.md)

- [Architektura náhledu tisku](../mfc/print-preview-architecture.md)

- [Ukázka](../visual-cpp-samples.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
