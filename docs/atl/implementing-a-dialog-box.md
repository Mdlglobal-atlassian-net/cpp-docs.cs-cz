---
title: Implementace dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319479"
---
# <a name="implementing-a-dialog-box"></a>Implementace dialogového okna

Dialogové okno atl do projektu atl lze přidat dvěma způsoby: použijte Průvodce dialogem ATL nebo ho přidejte ručně.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Přidání dialogového okna pomocí Průvodce dialogovým oknem atl

V [dialogovém okně Přidat třídu](../ide/add-class-dialog-box.md)vyberte objekt dialogového okna KNIHOVNY ATL a přidejte dialogové okno do projektu knihovny ATL. Podle potřeby vyplňte Průvodce dialogem atl a klepněte na **tlačítko Dokončit**. Průvodce přidá do projektu třídu odvozenou z [CAxDialogImpl.](../atl/reference/caxdialogimpl-class.md) Otevřete **zobrazení prostředků** z nabídky **Zobrazení,** vyhledejte dialogové okno a poklepáním jej otevřete v editoru prostředků.

> [!NOTE]
> Pokud je dialogové okno `CAxDialogImpl`odvozeno z aplikace , může být hostitelem ovládacích prvků ActiveX i Windows. Pokud nechcete, aby režie podpory ovládacího prvku ActiveX ve třídě dialogového okna, použijte místo toho [CSimpleDialog](../atl/reference/csimpledialog-class.md) nebo [CDialogImpl.](../atl/reference/cdialogimpl-class.md)

Obslužné rutiny zpráv a událostí lze přidat do třídy dialogu ze zobrazení třídy. Další informace naleznete [v tématu Přidání obslužné rutiny zprávy ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ruční přidání dialogového okna

Implementace dialogového okna je podobná implementaci okna. Odvozujete třídu z [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)nebo [CSimpleDialog](../atl/reference/csimpledialog-class.md) a deklarujete [mapu zprávy](../atl/message-maps-atl.md) pro zpracování zpráv. Je však nutné také zadat ID prostředku šablony dialogu v odvozené třídě. Vaše třída musí mít `IDD` datový člen volána pro uložení této hodnoty.

> [!NOTE]
> Když vytvoříte dialogové okno pomocí Průvodce dialogem ATL, průvodce automaticky přidá `IDD` člen jako typ **výčtu.**

`CDialogImpl`umožňuje implementovat modální nebo nemodální dialogové okno, které je hostitelem ovládacích prvků systému Windows. `CAxDialogImpl`umožňuje implementovat modální nebo nemodální dialogové okno, které je hostitelem ovládacích prvků ActiveX i Windows.

Chcete-li vytvořit modální dialogové `CDialogImpl`okno, vytvořte `CAxDialogImpl`instanci vaší odvozené (nebo odvozené) třídy a pak zavolejte metodu [DoModal.](../atl/reference/cdialogimpl-class.md#domodal) Chcete-li zavřít modální dialogové okno, zavolejte metodu [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) z obslužné rutiny zprávy. Chcete-li vytvořit nemodální dialogové okno, zavolejte metodu [Create](../atl/reference/cdialogimpl-class.md#create) místo `DoModal`. Chcete-li zničit nemodální dialogové okno, volejte [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Potopení události se automaticky provádí v [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implementujte obslužné rutiny zpráv dialogového `CWindowImpl`okna stejně jako obslužné rutiny v odvozené třídě. Pokud je vrácená hodnota specifická pro `LRESULT`zprávu, vraťte ji jako . Vrácené `LRESULT` hodnoty jsou mapovány podle atl pro správné zpracování správce dialogů systému Windows. Podrobnosti naleznete ve zdrojovém kódu [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) v atlwin.h.

## <a name="example"></a>Příklad

Následující třída implementuje dialogové okno:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Viz také

[Třídy oken](../atl/atl-window-classes.md)
