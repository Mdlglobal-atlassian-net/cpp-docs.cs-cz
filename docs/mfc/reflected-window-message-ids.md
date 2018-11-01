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
ms.openlocfilehash: 80cc7c6190a9467ca64bd0df7e55b6385a38ce5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588448"
---
# <a name="reflected-window-message-ids"></a>Identifikátory reflektovaných zpráv oken

Rychlý způsob, jak vytvořit ovládací prvek ActiveX nebo jiného specializovaného ovládacího prvku, je podtřídou časového období. Další informace najdete v tématu [knihovny MFC – ovládací prvky ActiveX: vytvoření podtřídy ovládacího prvku Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

Aby se zabránilo kontejneru ovládacího prvku příjem okno zprávy odesílané rozčleněné ovládací prvek Windows, [COleControl](../mfc/reference/colecontrol-class.md) vytvoří okno "reflector" zachytily určité zprávy okna a odeslat je zpátky do ovládacího prvku. Ovládacího prvku, v jeho proceduru okna můžete následně zpracovat tyto reflektované zprávy provedením akce, které jsou vhodné pro ovládací prvek ActiveX.

Následující tabulka uvádí zprávy, které jsou zachyceny a odpovídající zprávy, které odesílá okně reflector.

|Zprávy odesílané ovládacího prvku|Zpráva odrazí na ovládacím prvku|
|---------------------------------|--------------------------------------|
|[WM_COMMAND –](/windows/desktop/menurc/wm-command)|OCM_COMMAND –|
|[WM_CTLCOLORBTN](/windows/desktop/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN –|
|[WM_CTLCOLOREDIT](/windows/desktop/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT –|
|[WM_CTLCOLORDLG](/windows/desktop/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG –|
|[WM_CTLCOLORLISTBOX](/windows/desktop/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX –|
|[WM_CTLCOLORSCROLLBAR](/windows/desktop/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR –|
|[WM_CTLCOLORSTATIC](/windows/desktop/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC –|
|[WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem)|OCM_DRAWITEM –|
|[WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem)|OCM_MEASUREITEM –|
|[WM_DELETEITEM](/windows/desktop/Controls/wm-deleteitem)|OCM_DELETEITEM –|
|[WM_VKEYTOITEM](/windows/desktop/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM –|
|[WM_CHARTOITEM](/windows/desktop/Controls/wm-chartoitem)|OCM_CHARTOITEM –|
|[WM_COMPAREITEM](/windows/desktop/Controls/wm-compareitem)|OCM_COMPAREITEM –|
|[WM_HSCROLL](/windows/desktop/Controls/wm-hscroll)|OCM_HSCROLL –|
|[WM_VSCROLL](/windows/desktop/Controls/wm-vscroll)|OCM_VSCROLL –|
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY –|
|[WM_NOTIFY –](https://msdn.microsoft.com/library/windows/desktop/bb775583)|OCM_NOTIFY –|

> [!NOTE]
>  Pokud spustí v systému Win32, existuje několik typů WM_CTLCOLOR –\* může přijímat zprávy. Další informace najdete v tématu WM_CTLCOLORBTN WM_CTLCOLORDLG, WM_CTLCOLOREDIT, WM_CTLCOLORLISTBOX, WM_CTLCOLORMSGBOX, WM_CTLCOLORSCROLLBAR, WM_CTLCOLORSTATIC.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku systému Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)<br/>
[TN062: Reflexe zprávy pro ovládací prvky Windows](../mfc/tn062-message-reflection-for-windows-controls.md)

