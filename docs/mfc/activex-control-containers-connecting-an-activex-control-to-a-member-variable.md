---
title: 'Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: 2234647e933e37ff82845c4b40dc93cefeb55575
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446459"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné

Nejjednodušší způsob, jak přistupovat k ovládacího prvku ActiveX v rámci jeho kontejnerové aplikace ovládacího prvku je přidružení ovládacího prvku ActiveX k členské proměnné této třídy dialogového okna, která bude obsahovat ovládací prvek.

> [!NOTE]
>  To není jediný způsob, jak získat přístup vloženému ovládacímu prvku z v rámci třídy kontejneru, ale pro účely tohoto článku je dostačující.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Přidání členské proměnné třídy dialogového okna

1. Ze zobrazení tříd klikněte pravým tlačítkem na třídu hlavní dialogové okno otevřete místní nabídku. Například `CContainerDlg`.

1. V místní nabídce klikněte na tlačítko **přidat** a potom **přidat proměnnou**.

1. V Průvodce přidáním členské proměnné, klikněte na tlačítko **řídicí proměnná**.

1. V **ID ovládacího prvku** seznamu, vyberte ID ovládacího prvku vloženému ovládacímu prvku ActiveX. Například `IDC_CIRCCTRL1`.

1. V **název proměnné** pole, zadejte název.

   Například *m_circctl*.

1. Klikněte na tlačítko **Dokončit** potvrďte zvolené volby a ukončete Průvodce přidáním členské proměnné.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

