---
title: Implementace dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 1a3084d4655e173234d3bb6e8d411b28e8968377
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198050"
---
# <a name="implementing-a-dialog-box"></a>Implementace dialogového okna

Existují dva způsoby, jak dialogové okno Přidat do projektu ATL: použijte Průvodce dialogem ATL nebo ji přidat ručně.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Přidání dialogového okna pomocí Průvodce dialogem ATL

V [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md), vyberte objekt ATL Dialog dialogového okna Přidat do projektu ATL s Knihovnami. Průvodce dialogem ATL podle potřeby zadejte a klikněte na tlačítko **Dokončit**. Průvodce přidá třídu odvozenou z [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) do projektu. Otevřete **zobrazení prostředků** z **zobrazení** nabídku, vyhledejte dialogové okno a dvojím kliknutím ho otevřete v editoru prostředků.

> [!NOTE]
>  Pokud vaše dialogové okno je odvozena z `CAxDialogImpl`, může být hostitelem obou ActiveX a ovládacích prvků Windows. Pokud nechcete, aby nároky na podporu ovládacích prvků ActiveX do vaší třídy dialogového okna, použijte [CSimpleDialog](../atl/reference/csimpledialog-class.md) nebo [CDialogImpl](../atl/reference/cdialogimpl-class.md) místo.

Obslužné rutiny zpráv a událostí můžete přidat do vlastní třídy dialogového okna ze zobrazení tříd. Další informace najdete v tématu [Přidání popisovače zpráv knihovny ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ruční přidání dialogového okna

Implementace dialogového okna je podobný implementace okna. Odvodit třídu z buď [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), nebo [CSimpleDialog](../atl/reference/csimpledialog-class.md) a deklarovat [mapu zpráv](../atl/message-maps-atl.md) ke zpracování zpráv. Však musíte také zadat ID prostředku šablony dialogového okna v odvozené třídě. Vaše třída musí mít datový člen s názvem `IDD` pro uložení této hodnoty.

> [!NOTE]
>  Když vytvoříte dialogové okno pomocí Průvodce dialogem ATL, průvodce automaticky přidá `IDD` člena jako **výčtu** typu.

`CDialogImpl` umožňuje implementovat modální a nemodální dialogové okno, který je hostitelem ovládacích prvků Windows. `CAxDialogImpl` umožňuje implementovat modální a nemodální dialogové okno, který je hostitelem ovládacích prvků ActiveX a Windows.

Vytvoříte modální dialogové okno vytvořit instanci vaší `CDialogImpl`-odvozené (nebo `CAxDialogImpl`-odvozené) třídy a následně zavolat [DoModal](../atl/reference/cdialogimpl-class.md#domodal) – metoda. Chcete-li modální dialogové okno zavřete, zavolejte [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) metodu z obslužné rutiny zpráv. Chcete-li vytvořit nemodální dialogové okno, zavolejte [vytvořit](../atl/reference/cdialogimpl-class.md#create) metoda místo `DoModal`. Chcete-li zničit nemodální dialogové okno, zavolejte [destroywindow –](../atl/reference/cdialogimpl-class.md#destroywindow).

Zpracování událostí se provádí automaticky v [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Stejně jako u obslužných rutin v implementaci obslužné rutiny zpráv v dialogovém okně `CWindowImpl`-odvozené třídy. Pokud je návratová hodnota specifické pro zprávy, vraťte ho jako `LRESULT`. Vrácený `LRESULT` hodnoty jsou mapovány pomocí knihovny ATL pro správné zpracování správcem dialogového okna Windows. Podrobnosti najdete ve zdrojovém kódu pro [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) v atlwin.h.

## <a name="example"></a>Příklad

Následující třída implementuje dialog:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Viz také:

[Třídy oken](../atl/atl-window-classes.md)
