---
title: Identifikátory reflektovaných zpráv oken
ms.date: 11/04/2016
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
ms.openlocfilehash: 6d4ee3483bdfeb88951071bddb748671897a424b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754389"
---
# <a name="reflected-window-message-ids"></a>Identifikátory reflektovaných zpráv oken

Rychlý způsob, jak vytvořit ovládací prvek ActiveX nebo jiný specializovaný ovládací prvek, je podtřídy okna. Další informace naleznete v [tématu Ovládací prvky ActiveX knihovny MFC: Podřazení ovládacího prvku systému Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

Chcete-li zabránit kontejneru ovládacího prvku přijímat zprávy okna odeslané podtřídou ovládacího prvku systému Windows, [COleControl](../mfc/reference/colecontrol-class.md) vytvoří okno "reflektor" zachytit určité zprávy okna a odeslat je zpět do ovládacího prvku. Ovládací prvek v jeho okno postup, pak můžete zpracovat tyto odražené zprávy tím, že akce vhodné pro ovládací prvek ActiveX.

V následující tabulce jsou uvedeny zprávy, které jsou zachyceny a odpovídající zprávy, které odesílá okno reflektoru.

|Zpráva odeslaná ovládacím prvkem|Zpráva se odráží do ovládacího prvku|
|---------------------------------|--------------------------------------|
|[WM_COMMAND](/windows/win32/menurc/wm-command)|OCM_COMMAND|
|[WM_CTLCOLORBTN](/windows/win32/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN|
|[WM_CTLCOLOREDIT](/windows/win32/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT|
|[WM_CTLCOLORDLG](/windows/win32/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG|
|[WM_CTLCOLORLISTBOX](/windows/win32/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX|
|[WM_CTLCOLORSCROLLBAR](/windows/win32/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR|
|[WM_CTLCOLORSTATIC](/windows/win32/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC|
|[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)|OCM_DRAWITEM|
|[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)|OCM_MEASUREITEM|
|[WM_DELETEITEM](/windows/win32/Controls/wm-deleteitem)|OCM_DELETEITEM|
|[WM_VKEYTOITEM](/windows/win32/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM|
|[WM_CHARTOITEM](/windows/win32/Controls/wm-chartoitem)|OCM_CHARTOITEM|
|[WM_COMPAREITEM](/windows/win32/Controls/wm-compareitem)|OCM_COMPAREITEM|
|[WM_HSCROLL](/windows/win32/Controls/wm-hscroll)|OCM_HSCROLL|
|[WM_VSCROLL](/windows/win32/Controls/wm-vscroll)|OCM_VSCROLL|
|[WM_PARENTNOTIFY](/windows/win32/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY|
|[WM_NOTIFY](/windows/win32/controls/wm-notify)|OCM_NOTIFY|

> [!NOTE]
> Pokud je ovládací prvek spuštěn v systému Win32, existuje několik typů WM_CTLCOLOR\* zpráv, které může přijímat. Další informace naleznete v WM_CTLCOLORBTN, WM_CTLCOLORDLG, WM_CTLCOLOREDIT, WM_CTLCOLORLISTBOX, WM_CTLCOLORMSGBOX, WM_CTLCOLORSCROLLBAR, WM_CTLCOLORSTATIC.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku systému Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)<br/>
[TN062: Reflexe zprávy pro ovládací prvky Windows](../mfc/tn062-message-reflection-for-windows-controls.md)
