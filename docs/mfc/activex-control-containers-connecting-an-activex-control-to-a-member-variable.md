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
ms.openlocfilehash: 620a9ec58b3a5a8fcdac63626b81fbc4620de399
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371610"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné

Nejjednodušší způsob, jak získat přístup k ovládacímu prvku ActiveX z aplikace kontejneru ovládacího prvku, je přidružit ovládací prvek ActiveX k členské proměnné třídy dialogu, která bude ovládací prvek obsahovat.

> [!NOTE]
> Toto není jediný způsob, jak získat přístup k vložený ovládací prvek z v rámci třídy kontejneru, ale pro účely tohoto článku je dostačující.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Přidání členské proměnné do třídy dialogu

1. V zobrazení třídy otevřete místní nabídku kliknutím pravým tlačítkem myši na hlavní třídu dialogového okna. Například, `CContainerDlg`.

1. V místní nabídce klikněte na **Přidat** a potom na **Přidat proměnnou**.

1. V Průvodci přidáním členské proměnné klepněte na **položku Ovládací prvek**.

1. V seznamu **ID ovládacího prvku** vyberte ID ovládacího prvku vloženého ovládacího prvku ActiveX. Například, `IDC_CIRCCTRL1`.

1. Do pole **Název proměnné** zadejte název.

   Například *m_circctl*.

1. Klepnutím na **tlačítko Dokončit** přijměte své volby a ukončete Průvodce přidáním členské proměnné.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)
