---
title: ActiveX – kontejnery ovládacích prvků
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: e8340acafc81447052fcb8d90df8997e81dc4117
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394855"
---
# <a name="activex-control-containers"></a>ActiveX – kontejnery ovládacích prvků

Kontejneru ovládacího prvku ActiveX je kontejner, který podporuje ovládací prvky ActiveX a můžete začlenit do svých vlastních windows dialogová okna. Ovládací prvek ActiveX je opakovaně použitelná softwarová element, který můžete použít v mnoha projektů vývoje. Ovládací prvky umožňují uživatelům vaší aplikace přistupuje k databázím, monitorovat data a různých dle popisu v rámci vašich aplikací. Další informace o ovládacích prvků ActiveX naleznete v článku [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md).

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace najdete v tématu [ovládací prvky ActiveX](activex-controls.md).

Kontejnery ovládacích prvků obvykle trvá dva formuláře v projektu:

- Dialogová okna a podobné dialogové okno windows, jako je zobrazení formuláře, ve kterém se ovládací prvek ActiveX používá někde v dialogovém okně.

- Windows v aplikaci, ve kterém se ovládací prvek ActiveX používá v panelu nástrojů nebo jiného umístění v okně uživatele.

Vystavené ActiveX, kontejnerem ovládacího prvku komunikuje s ovládacím prvkem prostřednictvím [metody](../mfc/mfc-activex-controls-methods.md) a [vlastnosti](../mfc/mfc-activex-controls-properties.md). Tyto metody a vlastnosti, které jde přistupovat a upravovat kontejnerem ovládacího prvku, jsou přístupné prostřednictvím obálkovou třídu v projektu kontejneru ovládacího prvku ActiveX. Vložené ovládací prvky ActiveX lze také interagovat s kontejnerem ohlásí (odesílání) [události](../mfc/mfc-activex-controls-events.md) oznámit kontejneru došlo k akci. Ovládací prvek kontejneru můžete tak, aby fungoval na tato oznámení nebo ne.

Další články popisují několik témat, od vytvoření projektu kontejneru ovládacího prvku ActiveX na základní implementaci problémy související s kontejnery ovládacích prvků ActiveX vytvořeného pomocí jazyka Visual C++:

- [Vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)

- [Kontejnery pro ovládací prvky ActiveX](../mfc/containers-for-activex-controls.md)

- [Kontejnery ovládacích prvků ActiveX: Ruční povolení uzavření ovládacího prvku ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)

- [Kontejnery ovládacích prvků ActiveX: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku](../mfc/inserting-a-control-into-a-control-container-application.md)

- [Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [Kontejnery ovládacích prvků ActiveX: Zpracování událostí z ovládacího prvku ActiveX](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)

- [Kontejnery ovládacích prvků ActiveX: Zobrazení a úpravy vlastností ovládacích prvků](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)

- [Kontejnery ovládacích prvků ActiveX: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)

- [Kontejnery ovládacích prvků ActiveX: Použití ovládacích prvků v kontejneru bez dialogových oken](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)

Další informace o používání ovládacích prvků ActiveX v dialogovém okně najdete v tématu [editoru dialogového okna](../windows/dialog-editor.md) témata.

Seznam článků, které vysvětlují, podrobnosti o vývoji ovládacích prvků ActiveX pomocí jazyka Visual C++ a třídy ovládacích prvků ActiveX knihovny MFC naleznete v tématu [ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md). Články jsou seskupené podle funkčních kategorií.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
