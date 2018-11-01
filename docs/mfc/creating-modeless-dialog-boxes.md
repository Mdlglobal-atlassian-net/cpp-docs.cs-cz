---
title: Vytváření nemodálních dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 4cc2bc0ce54ad658a8bf13e70a8fa54479cbbf79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453701"
---
# <a name="creating-modeless-dialog-boxes"></a>Vytváření nemodálních dialogových oken

Pro nemodální dialogové okno je nutné zadat vlastní veřejný konstruktor ve vlastní třídy dialogového okna. Vytvoření nemodálního dialogového okna, zavolejte veřejný konstruktor a poté zavolejte objektu dialogového okna [vytvořit](../mfc/reference/cdialog-class.md#create) členská funkce se načíst prostředek dialogu. Můžete volat **vytvořit** během nebo po volání konstruktoru. Pokud má vlastnost prostředku dialogového okna **WS_VISIBLE**, okamžitě se zobrazí dialogové okno. Pokud ne, je nutné volat jeho [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) členskou funkci.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

