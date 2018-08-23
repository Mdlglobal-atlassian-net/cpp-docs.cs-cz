---
title: Projeví identifikátory zpráv oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 968a8560447b0bf8f74e94f8b492e1de7192df76
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465488"
---
# <a name="reflected-window-message-ids"></a>Identifikátory reflektovaných zpráv oken
Rychlý způsob, jak vytvořit ovládací prvek ActiveX nebo jiného specializovaného ovládacího prvku, je podtřídou časového období. Další informace najdete v tématu [knihovny MFC – ovládací prvky ActiveX: vytvoření podtřídy ovládacího prvku Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
 Aby se zabránilo kontejneru ovládacího prvku příjem okno zprávy odesílané rozčleněné ovládací prvek Windows, [COleControl](../mfc/reference/colecontrol-class.md) vytvoří okno "reflector" zachytily určité zprávy okna a odeslat je zpátky do ovládacího prvku. Ovládacího prvku, v jeho proceduru okna můžete následně zpracovat tyto reflektované zprávy provedením akce, které jsou vhodné pro ovládací prvek ActiveX.  
  
 Následující tabulka uvádí zprávy, které jsou zachyceny a odpovídající zprávy, které odesílá okně reflector.  
  
|Zprávy odesílané ovládacího prvku|Zpráva odrazí na ovládacím prvku|  
|---------------------------------|--------------------------------------|  
|[WM_COMMAND –](http://msdn.microsoft.com/library/windows/desktop/ms647591)|OCM_COMMAND –|  
|[WM_CTLCOLORBTN](http://msdn.microsoft.com/library/windows/desktop/bb761849)|OCM_CTLCOLORBTN –|  
|[WM_CTLCOLOREDIT](http://msdn.microsoft.com/library/windows/desktop/bb761691)|OCM_CTLCOLOREDIT –|  
|[WM_CTLCOLORDLG](http://msdn.microsoft.com/library/windows/desktop/ms645417)|OCM_CTLCOLORDLG –|  
|[WM_CTLCOLORLISTBOX](http://msdn.microsoft.com/library/windows/desktop/bb761360)|OCM_CTLCOLORLISTBOX –|  
|[WM_CTLCOLORSCROLLBAR](http://msdn.microsoft.com/library/windows/desktop/bb787573)|OCM_CTLCOLORSCROLLBAR –|  
|[WM_CTLCOLORSTATIC](http://msdn.microsoft.com/library/windows/desktop/bb787524)|OCM_CTLCOLORSTATIC –|  
|[WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923)|OCM_DRAWITEM –|  
|[WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925)|OCM_MEASUREITEM –|  
|[WM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb761362)|OCM_DELETEITEM –|  
|[WM_VKEYTOITEM](http://msdn.microsoft.com/library/windows/desktop/bb761364)|OCM_VKEYTOITEM –|  
|[WM_CHARTOITEM](http://msdn.microsoft.com/library/windows/desktop/bb761358)|OCM_CHARTOITEM –|  
|[WM_COMPAREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775921)|OCM_COMPAREITEM –|  
|[WM_HSCROLL](http://msdn.microsoft.com/library/windows/desktop/bb787575)|OCM_HSCROLL –|  
|[WM_VSCROLL](http://msdn.microsoft.com/library/windows/desktop/bb787577)|OCM_VSCROLL –|  
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY –|  
|[WM_NOTIFY –](http://msdn.microsoft.com/library/windows/desktop/bb775583)|OCM_NOTIFY –|  
  
> [!NOTE]
>  Pokud spustí v systému Win32, existuje několik typů WM_CTLCOLOR –\* může přijímat zprávy. Další informace najdete v tématu WM_CTLCOLORBTN WM_CTLCOLORDLG, WM_CTLCOLOREDIT, WM_CTLCOLORLISTBOX, WM_CTLCOLORMSGBOX, WM_CTLCOLORSCROLLBAR, WM_CTLCOLORSTATIC.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: Vytvoření podtřídy ovládacího prvku Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)   
 [TN062: Reflexe zprávy pro ovládací prvky Windows](../mfc/tn062-message-reflection-for-windows-controls.md)

