---
title: Použití běžného ovládacího prvku jako podřízeného okna
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
ms.openlocfilehash: 690b48cf50e95265aaf5bdd454e2881b8f5fab3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655127"
---
# <a name="using-a-common-control-as-a-child-window"></a>Použití běžného ovládacího prvku jako podřízeného okna

Některé z běžných ovládacích prvků Windows můžete použít jako podřízeného okna ostatní okna. Následující postup popisuje, jak dynamicky vytvořit běžného ovládacího prvku a následně s ním pracovat.

### <a name="to-use-a-common-control-as-a-child-window"></a>Použití běžného ovládacího prvku jako podřízeného okna

1. Definování ovládacího prvku v související třídy nebo obslužná rutina.

1. Použití přepsání ovládacího prvku [CWnd::Create](../mfc/reference/cwnd-class.md#create) metodu pro vytvoření ovládacího prvku Windows.

1. Po vytvoření ovládacího prvku (co nejdříve, jako `OnCreate` obslužná rutina Pokud podtřídy ovládacího prvku), můžete upravit ovládací prvek pomocí jeho členské funkce. Přečtěte si popisy jednotlivých ovládacích prvků na [ovládací prvky](../mfc/controls-mfc.md) podrobné informace o metodách.

1. Až skončíte s ovládacím prvkem, použijte [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) ke zničení ovládacího prvku.

## <a name="see-also"></a>Viz také

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

