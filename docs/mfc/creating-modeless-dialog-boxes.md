---
title: Vytváření nemodálních dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 71cca82e667ddbf5cfc4c2abb5880cd69c7fafae
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266351"
---
# <a name="creating-modeless-dialog-boxes"></a>Vytváření nemodálních dialogových oken

Pro nemodální dialogové okno je nutné zadat vlastní veřejný konstruktor ve vlastní třídy dialogového okna. Vytvoření nemodálního dialogového okna, zavolejte veřejný konstruktor a poté zavolejte objektu dialogového okna [vytvořit](../mfc/reference/cdialog-class.md#create) členská funkce se načíst prostředek dialogu. Můžete volat **vytvořit** během nebo po volání konstruktoru. Pokud má vlastnost prostředku dialogového okna **WS_VISIBLE**, okamžitě se zobrazí dialogové okno. Pokud ne, je nutné volat jeho [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) členskou funkci.

## <a name="see-also"></a>Viz také:

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
